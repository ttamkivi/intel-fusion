# ⚡ Intel Fusion Tool v2.1

**NATO G2 Intelligence Processing for Air-Gapped Networks**

Converts raw battlefield chat messages (SALUTE reports, UAV observations, scout reports) into a structured, searchable intelligence database. Runs entirely in your browser — no internet, no server, no installation. Designed for NATO exercise fusion cells on classified networks.

## Quick Start

1. Open `intel_fusion.html` in Chrome or Edge (90+)
2. Open `test_chat_simulator.html` in a second tab for demo data
3. Click **📡 Start Auto-Scan** to begin pulling messages
4. Generate reports from the **📄 Generate Intelligence Report** panel

No installation. No internet. No admin rights.

## What It Does

**Input** — Raw battlefield chatter from multiple chat channels:

- Auto-scan via BroadcastChannel API (pulls from open chat tabs every 5–60s)
- Manual paste for offline or clipboard workflows
- Parses free-text, SALUTE format, and coordinate references (MGRS + decimal)

**Processing** — Extracts structured intelligence:

- Date-Time Group (DTG) in Zulu format
- MGRS coordinates (zones 34V–35V for Estonia/Baltics)
- Activity classification (Movement, Engagement, Position, Observation, Staging)
- Equipment identification with NATO reference data
- Unit and strength estimation, priority assignment (HIGH / ROUTINE)
- Duplicate detection via DJB2 content hashing

**Output** — 10 NATO-standard report formats:

- **Tactical:** INTSUM, SPOTREP, SITREP, INTREP, SALUTE
- **Targeting & BDA:** BDA (AJP-3.9), MISREP
- **Higher HQ:** DIB, OPINTEL, PIR Tracker

Plus: formatted HTML reports with classification banners, big-screen briefing presentation mode, tactical SVG map of Estonia with plotted symbols, JSON save/load, Excel (XLS) and TSV export, T-day timeline tracking.

## Architecture

```
┌─────────────────────────────────────────────┐
│            Single HTML File (~160KB)         │
│  CSS + HTML + JavaScript (IIFE pattern)      │
│  No build step · No dependencies · No server │
└──────────────────┬──────────────────────────┘
                   │ BroadcastChannel API (PULL model)
┌──────────────────┴──────────────────────────┐
│  Chat Simulator / Chat Tabs (separate tabs)  │
│  Responds to INTEL_SCRAPE_REQUEST messages   │
└─────────────────────────────────────────────┘
```

Design decisions: single file (no external dependencies), no localStorage (data in session memory only, browser close = clean slate), PULL architecture (Intel Fusion requests from chat tabs), air-gap safe (strict CSP, `connect-src 'none'`).

## Tactical Map

Geographically accurate SVG map of Estonia with ~200 coordinate points:

- Mainland coastline, Saaremaa, Hiiumaa, Muhu, Vormsi islands
- Lake Peipus and Pihkva järv
- 17 cities at real lat/lon positions
- Coordinate grid with degree labels
- Neighbouring countries (Russia, Latvia)
- Water bodies (Gulf of Finland, Gulf of Riga, Baltic Sea)

Records with valid MGRS coordinates appear as clickable symbols. Click a coordinate in the records table to flash-highlight it on the map.

## G2 Staff Roles

24 NATO G2 staff roles across 8 functional cells are available in the admin panel: G2 Leadership, All-Source Fusion, Collection Management & Dissemination, ISR Cell, HUMINT Cell, SIGINT/EW Cell, CI/OSINT Cell, and Targeting/BDA Cell.

## Exercise Scenarios (Test Simulator)

| Scenario | Description |
|----------|-------------|
| NORTHERN SHIELD | Conventional ground force defence — BTG movements, artillery positions |
| ISLAND FORTRESS | Island defence (Saaremaa) — amphibious threats, naval activity |
| GRAY STORM | Hybrid warfare — cyber attacks, civil unrest, information operations |

## Repository Structure

```
intel-fusion/
  intel_fusion.html          # The application (single file, open in browser)
  test_chat_simulator.html   # Battle scenario chat simulator for testing
  README.md                  # This file
  SECURITY.md                # Security architecture & CISO deployment guide
  docs/
    QUICK_START.txt           # Getting started guide
    bookmarklet_setup.txt     # Browser automation guide
    SECURITY_AUDIT.md         # v2.0 audit report (historical)
    ADDITIONAL_RESOURCES.md   # Curated open-source references
  brain/                      # Reference documents (knowledge base)
    SYSTEM_PROMPT.md          # Claude AI project instructions
    README.md                 # Annotated list of reference materials
    *.pdf                     # UNCLASSIFIED reference documents
```

## Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 90+ | Full support |
| Edge | 90+ | Full support |
| Firefox | 90+ | Full support |
| Safari | 15.4+ | BroadcastChannel supported from 15.4 |

Requires: `crypto.randomUUID()`, `BroadcastChannel`, ES6+ syntax.

## Security

See [SECURITY.md](SECURITY.md) for the full security architecture, CISO deployment checklist, and threat model.

Summary: CSP blocks all external resources and network requests. All user input sanitised via `escapeHTML()`. Formula injection protection on all exports. No persistent storage. Admin PIN with rate limiting. Zero external dependencies. See the security document for the complete audit trail.

## Classification

- **Tool itself**: UNCLASSIFIED
- **Can process**: Any classification level (data stays local, never transmitted)
- **Exports**: Mark per your data handling procedures

## Version History

| Version | Date | Changes |
|---------|------|---------|
| v2.1.1 | 8 Apr 2026 | Security hardening (XSS fix in onclick, XLS formula injection, CSP tightened to img-src 'none', PIN rate limiting), high-quality Estonia map (200+ points, 5 islands, Lake Peipus), QA + security audit, documentation |
| v2.1 | 7 Apr 2026 | Auto-scan with BroadcastChannel, 10 NATO reports, big-screen briefing, T-day timeline, tactical map, 24 G2 roles, JSON save/load, XLS export, bilingual EN/ET |
| v2.0 | 7 Apr 2026 | Security hardening (XSS, CSP, formula injection, PostMessage validation), IIFE encapsulation |
| v1.0 | Jan 2026 | Initial release |

## License

For NATO exercise use. Not for public distribution of classified data.

---

Built for Estonian Defence Forces G2 fusion cell exercises.
