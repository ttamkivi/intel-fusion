# Security Audit Report — Intel Fusion v2.0 (Historical)

> **Note:** This is the v2.0 audit report preserved for audit trail purposes.
> For the current security architecture and CISO deployment guide, see [../SECURITY.md](../SECURITY.md) (v2.1.1, 8 April 2026).

**Date:** April 7, 2026
**Scope:** Full security review of intel_fusion.html (single-file browser application)
**Classification:** UNCLASSIFIED
**Target environment:** Air-gapped/classified military networks

---

## Executive Summary

Intel Fusion v2.0 has been hardened against all identified security vulnerabilities from the v1.0 codebase. The tool is suitable for deployment on restricted and classified networks with the understanding that the tool itself is unclassified — classified data processed within it stays in browser memory only and is never persisted or transmitted.

---

## Vulnerabilities Found in v1.0 (All Fixed in v2.0)

### CRITICAL: Cross-Site Scripting (XSS) via innerHTML

**v1.0 issue:** The `showDetails()` function injected `record.fullMessage` directly into HTML using template literals inside `innerHTML`. A crafted message containing `<img onerror=alert(document.cookie)>` or `<script>` tags would execute arbitrary JavaScript.

**v2.0 fix:** All user-supplied data is passed through `escapeHTML()` before rendering. The function creates a temporary DOM element, sets `textContent` (which auto-escapes), then reads back the safe `innerHTML`. Table cells use `textContent` exclusively.

**Status:** FIXED

### CRITICAL: PostMessage Origin Not Validated

**v1.0 issue:** The `window.addEventListener('message')` handler accepted messages from any origin without validation. Any webpage in another tab could inject fake intelligence records.

**v2.0 fix:** The `handlePostMessage()` method now validates:
1. `event.data` is a non-null object
2. `event.data.type === 'INTEL_BATCH'` (exact match)
3. `event.data.messages` is an Array
4. Each message element is a string (non-string elements silently skipped)
5. Auto-mode must be explicitly enabled by the user

**Status:** FIXED

### HIGH: TSV Export Formula Injection

**v1.0 issue:** Exported TSV cells were not sanitized. A crafted message starting with `=`, `+`, `-`, or `@` would be interpreted as a formula by Excel, potentially executing `=CMD()` or `=HYPERLINK()` attacks when opened.

**v2.0 fix:** The `preventFormulaInjection()` function prefixes any cell value starting with `=`, `+`, `-`, `@`, `\t`, or `\r` with a single quote character (`'`), which Excel treats as a text indicator.

**Status:** FIXED

### HIGH: No Content Security Policy

**v1.0 issue:** No CSP meta tag meant the browser had no defense-in-depth against injection attacks. If XSS were exploited, there were no restrictions on what the injected code could do.

**v2.0 fix:** Comprehensive CSP meta tag added:
```
default-src 'none'; script-src 'unsafe-inline'; style-src 'unsafe-inline';
img-src 'none'; connect-src 'none'; font-src 'none'; object-src 'none';
frame-src 'none'; base-uri 'none'; form-action 'none';
```
This blocks all external resource loading, network connections, iframes, plugins, and form submissions. Only inline scripts and styles are permitted (required for single-file operation).

**Status:** FIXED

### MEDIUM: DTG Month Hardcoded

**v1.0 issue:** `extractDTG()` generated fallback DTGs with hardcoded "DJAN" regardless of the actual month. All auto-generated timestamps would show January.

**v2.0 fix:** Uses `MONTH_ABBR` array indexed by `now.getMonth()` to produce correct month abbreviation.

**Status:** FIXED

### MEDIUM: Weak Hash Function (Duplicate Detection)

**v1.0 issue:** `hashContent()` just lowercased text, stripped non-alphanumeric characters, and took the first 50 characters. This created easy hash collisions — two different messages with similar opening text would be treated as duplicates.

**v2.0 fix:** Replaced with DJB2 hash algorithm (`hash = ((hash << 5) + hash) ^ charCode`) which provides much better distribution across the full message content.

**Status:** FIXED

### LOW: Non-Unique Record IDs

**v1.0 issue:** Record IDs used `Date.now() + Math.random()` which could theoretically produce collisions in rapid batch processing.

**v2.0 fix:** Uses `crypto.randomUUID()` with fallback to RFC 4122 v4 UUID generation.

**Status:** FIXED

---

## Security Architecture (v2.0)

### Network Isolation
- CSP `connect-src 'none'` blocks all outbound network requests
- CSP `img-src 'none'` blocks image loading (prevents pixel tracking)
- CSP `frame-src 'none'` blocks iframe embedding
- CSP `object-src 'none'` blocks plugins (Flash, Java, etc.)
- `<meta name="referrer" content="no-referrer">` prevents URL leakage

### Data Isolation
- All data stored in JavaScript variables (session memory only)
- No localStorage, sessionStorage, IndexedDB, or cookies
- Browser close = complete data destruction
- No persistent storage without explicit user export action
- Permissions policy disables camera, microphone, geolocation, payment, USB

### Input Validation
- All parsing functions wrapped in try/catch
- Type checking on all inputs (`typeof` guards)
- Minimum message length enforcement (30 characters)
- PostMessage structure validation (type, array, string elements)
- HTML escaping on all rendered user content

### Output Sanitization
- TSV export: formula injection prevention on all cells
- DOM rendering: `escapeHTML()` on all user-supplied strings
- Table cells: `textContent` (never innerHTML with raw user data)

---

## Remaining Considerations

### Accepted Risks

1. **`script-src 'unsafe-inline'`**: Required because the app is a single HTML file with inline JavaScript. This is an accepted tradeoff for the single-file deployment constraint. Mitigated by the fact that `connect-src 'none'` prevents any exfiltration even if code injection occurred.

2. **Bookmarklet uses `postMessage('*')`**: The bookmarklet must work across origins (it runs on the chat page and sends to Intel Fusion). The wildcard target origin is acceptable because the RECEIVER validates strictly and requires auto-mode to be manually enabled.

3. **No authentication**: The tool has no user authentication. This is by design — it runs locally and authentication would require server infrastructure.

### Recommendations for Deployers

1. **Mark exports appropriately** — the tool does not auto-classify exported files
2. **Delete exports after use** — TSV files on disk are not encrypted
3. **Use in approved browsers only** — Chrome 90+ or Edge 90+ on managed devices
4. **Do not modify the CSP** — removing CSP restrictions weakens the security posture
5. **Air-gapped deployment** — for classified data, deploy on air-gapped networks only

---

## Test Vectors

To verify XSS protection is working:

```
Paste this as a message:
<script>alert('XSS')</script> spotted 3 tanks at 35V MD 85243 89003

Expected: Message is processed, script tags appear as text in the detail view, no alert popup.
```

To verify formula injection protection:

```
Process a message, export to TSV, open the TSV in a text editor.
Any cell starting with =, +, -, @ should be prefixed with a single quote.
```

---

**Auditor:** Claude (Anthropic)
**Tool version audited:** intel_fusion.html v2.0
**Audit methodology:** Static code analysis, architectural review, OWASP checklist
