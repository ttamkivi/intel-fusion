# Intel Fusion Tool v2.0

**Military Intelligence Processing System** — converts unstructured battlefield chat messages into a structured, searchable intelligence database. Runs entirely in the browser with zero external dependencies.

## What It Does

Intel Fusion ingests raw battlefield chat messages (NATO APP-11 SALUTE format or casual free-text), parses and extracts intelligence elements, stores them in an in-memory database, and exports to TSV/Excel format.

**From this:**
```
UAV2 spotted 3 tanks moving north, grid 35V MD 85243 89003
```

**To this:**

| DTG | Coordinate | Reporter | Activity | Equipment | Priority |
|-----|-----------|----------|----------|-----------|----------|
| 071545APR2026 | 35V MD 85243 89003 | UAV2 | MOVEMENT | TANK | ROUTINE |

## Quick Start

1. Open `intel_fusion.html` in Chrome or Edge
2. Paste chat messages into the text box
3. Click **Process & Add**
4. Done — view, filter, search, and export your intelligence database

No installation. No internet required. No admin rights needed.

## Features

- **Parsing engine**: Extracts coordinates (MGRS + decimal), equipment types, activity classification, unit strength, priority levels, and reporter callsigns
- **Duplicate detection**: Content hashing prevents re-processing the same message
- **Real-time filters**: Priority, activity type, and free-text search across all fields
- **Export**: One-click TSV download (Excel/SharePoint compatible) with formula injection protection
- **Copy to clipboard**: Quick TSV copy for pasting into other tools
- **Bookmarklet auto-mode**: Auto-extract messages from browser chat tabs via PostMessage
- **Mobile responsive**: Works on phones and tablets
- **Statistics dashboard**: Total records, high-priority count, movements, engagements

## Security

This tool was built for use on **air-gapped and classified networks**. Security is non-negotiable.

- Zero external network calls (Content Security Policy enforced)
- No localStorage, sessionStorage, or cookies — session memory only, clears on close
- No telemetry, analytics, tracking, or persistent storage
- All user content HTML-escaped to prevent XSS injection
- PostMessage handler validates message structure strictly
- TSV export sanitizes against Excel formula injection (`=`, `+`, `-`, `@` prefixed with `'`)
- Referrer policy: `no-referrer`
- Permissions policy: camera, microphone, geolocation, payment, USB all disabled
- See [SECURITY_AUDIT.md](docs/SECURITY_AUDIT.md) for the full audit report

## Deployment

| Scenario | How |
|----------|-----|
| Personal use | Open `intel_fusion.html` locally |
| Team | Upload to SharePoint, share the link |
| Unit network | Copy to shared drive |
| Air-gapped | Copy the single HTML file via approved transfer |

**Requirements:** Chrome 90+ or Edge 90+, JavaScript enabled. Nothing else.

## Repository Structure

```
intel-fusion/
  intel_fusion.html          # The application (single file, open in browser)
  test_chat_simulator.html   # Battle scenario chat simulator for testing
  README.md                  # This file
  docs/
    QUICK_START.txt           # Getting started in 1 minute
    bookmarklet_setup.txt     # Browser automation guide
    SECURITY_AUDIT.md         # Full security audit report
    ADDITIONAL_RESOURCES.md   # Curated open-source reference materials
    README_v1.txt             # Original v1.0 readme (archived)
  brain/                      # Reference documents (the knowledge base)
    SYSTEM_PROMPT.md            # Claude AI project instructions (the "brain" prompt)
    README.md                   # Annotated list of all reference materials + online resources
    *.pdf                       # 9 UNCLASSIFIED reference documents (see brain/README.md)
```

## Brain (Learning Materials)

The `brain/` folder contains the reference documents used to build and validate Intel Fusion. See [brain/README.md](brain/README.md) for the complete annotated list.

## Use Cases

- Battalion TOC intelligence screening
- Division G2 fusion operations
- Forward observer teams
- UAV operations monitoring
- Multinational NATO operations (eFP, JEF)

## Classification

- **Tool itself**: UNCLASSIFIED
- **Can process**: Any classification level (data stays local, never transmitted)
- **Exports**: Mark per your data handling procedures

## Version History

| Version | Date | Changes |
|---------|------|---------|
| v2.1 | April 2026 | Auto-scan scheduler with BroadcastChannel, JSON save/load, NATO report generation (INTSUM/SPOTREP/SITREP), SharePoint XLS export, battle scenario test simulator, EST/ENG language toggle, equipment reference links |
| v2.0 | April 2026 | Security hardening (XSS, CSP, formula injection, PostMessage validation), decimal coordinate support, proper DTG month, DJB2 hashing, IIFE encapsulation, keyboard accessibility, toast notifications, copy-to-clipboard |
| v1.0 | January 2026 | Initial release |

## License

This tool is provided as-is for military intelligence processing. Distribute via approved channels only.
