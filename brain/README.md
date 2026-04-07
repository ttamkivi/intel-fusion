# Brain — Intel Fusion Reference Documents

This folder contains the reference documents (the "knowledge base") used to build, validate, and maintain the Intel Fusion tool. These documents provide domain context for military intelligence processing, Russian military capabilities, NATO operational frameworks, and interoperability requirements.

## Included Documents

### 1. OverlookedAllyUA.pdf
**Military Review: U.S.-Estonian Task Force Voit Operations**
Source for interoperability requirements and operational context. Documents the practical challenges of multinational intelligence sharing during combined operations in the Baltic region.

### 2. IOP2019U021801Final.pdf
**CNA Paper: Russian C4/ISR Systems and Reconnaissance-Fire Contours**
Technical analysis of Russian command, control, communications, computers, intelligence, surveillance, and reconnaissance systems. Directly relevant for understanding the threat systems that Intel Fusion tracks — how Russian forces detect, target, and engage.

### 3. AWGRussianNewWarfareHandbook.pdf
**Asymmetric Warfare Group: Russian New Generation Warfare Handbook**
Comprehensive AWG handbook on Russian tactics, techniques, and procedures (TTPs). Key reference for understanding enemy intelligence collection targets and the types of battlefield reports Intel Fusion processes.

### 4. The_enhanced_Forward_Presence_...pdf
**NATO Defense College: Enhanced Forward Presence Policy Brief**
Policy analysis of NATO's eFP deployment model. Provides multinational operational context — Intel Fusion is designed for exactly these types of multinational formations where intelligence sharing across national contingents is critical.

### 5. MNATO2026_MC_BGG.pdf
**Multinational NATO 2026 Context Document**
Strategic context for NATO multinational operations in the 2026 timeframe. Relevant for understanding the operational environment where Intel Fusion would be deployed.

### 6. CBP9450.pdf
**UK Commons Library: NATO Eastern Flank Reinforcement**
Parliamentary briefing on NATO's eastern flank reinforcement. Provides political and military context for the Baltic and Eastern European operational theater.

### 7. October20122C20202320Russian20Orbat_Final.pdf
**ISW: Russian Ground Forces Order of Battle**
Authoritative open-source reference for Russian unit types, equipment designations, and organizational structure. Primary source for validating Intel Fusion's equipment recognition database (T-72, T-80, T-90, BMP, BTR, 2S19, etc.).

### 8. European_Defence_Agency__EDSTAR.pdf
**EDA EDSTAR Document**
European Defence Agency standards and technology context. Relevant for understanding European defence interoperability requirements.

### 9. default.pdf
**UK Defence Industrial Strategy**
Defence industrial strategy context. Background on the broader defence technology and procurement landscape.

## Additional Open-Source Resources

The following publicly available materials complement the brain documents. These are not included in the repo but are freely accessible online.

### SALUTE Reporting Standards
- [The SALUTE Report (PDF)](http://davidbrentthompson.com/Military/ScrapBook-Collections-Miscellaneous/Guidelines%20Instructions%20%20Procedures%20and%20Related/The%20SALUTE%20Report.pdf) — Comprehensive format guide
- [FM 21-75 Chapter 6: Combat Intelligence](https://www.globalsecurity.org/military/library/policy/army/fm/21-75/Ch6.htm) — Army field manual on intelligence reporting
- [SALUTE Report Training (GlobalSecurity)](https://www.globalsecurity.org/military/library/report/call/call_96-1_ct3-4art.htm) — CTC training bulletin
- [iSALUTE (U.S. Army INSCOM)](https://www.usainscom.army.mil/iSALUTE/iSALUTEFORM/) — Interactive SALUTE form tool

### HUMINT Collection Standards
- [FM 2-22.3: HUMINT Collector Operations (State Dept)](https://2009-2017.state.gov/documents/organization/150085.pdf) — Official Army field manual
- [FM 2-22.3 (Marines.mil)](https://www.marines.mil/Portals/1/Publications/FM%202-22.3%20%20Human%20Intelligence%20Collector%20Operations_1.pdf) — Marine Corps edition

### MGRS Coordinate System
- [Quick Guide to MGRS (maptools.com)](https://maptools.com/tutorials/mgrs/quick_guide) — Practical quick reference
- [NGA Coordinate Systems](https://earth-info.nga.mil/index.php?dir=coordsys&action=coordsys) — National Geospatial-Intelligence Agency official reference
- [Complete MGRS Guide (ITS Tactical)](https://www.itstactical.com/skillcom/navigation/the-complete-guide-to-land-navigation-with-the-military-grid-reference-system/) — Comprehensive tutorial

### NATO Military Symbology & Standards
- [NATO APP-6 Symbols (1986)](https://www.orbat85.nl/documents/APP-6%20NATO%20Symbols%201986.pdf) — Original UNCLASSIFIED APP-6
- [NATO APP-6(C) May 2011 (Internet Archive)](https://ia601602.us.archive.org/22/items/23-miscellanea/APP-6(C)%20NATO%20Joint%20Military%20Symbology%20-%20May%202011.pdf) — Joint military symbology standard
- [AJP-2.1: Allied Joint Doctrine for Intelligence (NATO JADL)](https://jadl.act.nato.int/ILIAS/data/testclient/lm_data/lm_152845/Linear/JISR04222102/sharedFiles/AJP21.pdf) — NATO intelligence procedures
- [NATO STANAGs List (April 2019)](https://api.army.mil/e2/c/downloads/2023/01/31/daf24e67/nato-standardization-agreements-apr-19-public.pdf) — Comprehensive STANAG directory
- [STANAG 2022 Discussion (DTIC)](https://apps.dtic.mil/sti/tr/pdf/ADA428653.pdf) — Information credibility standards

### Russian Military Order of Battle
- [ISW Russian Ground Forces ORBAT](https://www.understandingwar.org/backgrounder/russian-regular-ground-forces-order-battle-russian-military-101) — Authoritative open-source reference
- [ISW-CTP Ground Forces OOB (PDF)](https://www.criticalthreats.org/wp-content/uploads/2018/03/Russian-Ground-Forces-OOB_ISW-CTP.pdf) — Detailed analysis
- [U.S. Army TRADOC Russian Military Quick Reference](https://rdl.train.army.mil/catalog-ws/view/100.ATSC/80679288-2471-4B93-B921-CA4B04BF74FF-1625682681274/gta20_10_001.pdf) — Official Army training reference
- [Battle Order Russia](https://www.battleorder.org/russia) — Interactive unit organization reference

### OSINT Methodology
- [Open-Source Intelligence (Wikipedia)](https://en.wikipedia.org/wiki/Open-source-intelligence) — OSINT principles overview
- [OSINT Framework (BitSight)](https://www.bitsight.com/learn/cti/osint-framework) — Collection framework and tools

### 10. SYSTEM_PROMPT.md
**Claude AI Project System Prompt for Intel Fusion**
The complete system prompt / project instructions for use with Claude.ai Projects or Claude Coworker. Gives Claude full context about the technical stack, security requirements, parsing capabilities, deployment constraints, and source documents. Copy into your Claude Project's "Project Instructions" field.

---

## US Army Intelligence Doctrine (Online)

These are freely available US Army field manuals directly relevant to intelligence processing:

- [FM 2-0: Intelligence (2004)](https://www.bits.de/NRANEU/others/amd-us-archive/fm2-0(04).pdf) — Army keystone manual for military intelligence doctrine
- [FM 2-0: Intelligence (2023, Army Pubs)](https://armypubs.army.mil/epubs/DR_pubs/DR_a/ARN39259-FM_2-0-000-WEB-2.pdf) — Latest edition
- [FM 34-2: Collection Management](https://www.bits.de/NRANEU/others/amd-us-archive/fm34-2(94).pdf) — Intelligence collection management procedures
- [FM 2-22.3: HUMINT Collector Operations](https://2009-2017.state.gov/documents/organization/150085.pdf) — Human intelligence collection
- [CCIR Fires Perspective (JCS)](https://www.jcs.mil/Portals/36/Documents/Doctrine/fp/ccir_fp.pdf) — Commander's Critical Information Requirements

## NATO Intelligence Doctrine (Online)

- [AJP-2.1: Allied Joint Doctrine for Intelligence Procedures](https://jadl.act.nato.int/ILIAS/data/testclient/lm_data/lm_152845/Linear/JISR04222102/sharedFiles/AJP21.pdf) — NATO intelligence cycle
- [AJP-2.7: Allied Joint Doctrine for Reconnaissance & Surveillance](https://jadl.act.nato.int/ILIAS/data/testclient/lm_data/lm_152845/Linear/JISR04222102/sharedFiles/AJP27.pdf) — NATO R&S procedures
- [AIntP-14: NATO Intelligence Standards](https://jadl.act.nato.int/ILIAS/data/testclient/lm_data/lm_152845/Linear/JISR04222102/sharedFiles/AIntP14.pdf) — Intelligence interoperability
- [APP-11 NATO Message Catalogue](https://systematic.com/int/industries/defence/products/domains/interoperability/app11-and-adatp3/) — Message Text Format standard (overview)

## Russian Military Equipment & ORBAT (Online)

- [U.S. Army TRADOC: Russian Military Quick Reference (GTA 20-10-001)](https://rdl.train.army.mil/catalog-ws/view/100.ATSC/80679288-2471-4B93-B921-CA4B04BF74FF-1625682681274/gta20_10_001.pdf) — Official Army equipment ID cards
- [Worldwide Equipment ID Cards: Russia (FAS/IRP)](https://irp.fas.org/doddir/army/id-russia.pdf) — Visual identification guide
- [ISW Russian Ground Forces Interactive ORBAT](https://storymaps.arcgis.com/stories/6d9825cbafcd4cbf91cb6ce80d9e3f0f) — Interactive map with unit locations
- [Battle Order: Russia](https://www.battleorder.org/russia) — Unit organization reference
- [List of Equipment of Russian Ground Forces (Wikipedia)](https://en.wikipedia.org/wiki/List_of_equipment_of_the_Russian_Ground_Forces) — Comprehensive equipment listing
- [Army Recognition: Russian Vehicle Analysis](https://www.armyrecognition.com/news/army-news/2025/exclusive-report-full-analysis-of-all-combat-vehicles-displayed-at-russias-2025-victory-day-military-parade) — 2025 Victory Day parade vehicle analysis
- [TRADOC Signature of Equipment: Russian Air Defense](https://oe.tradoc.army.mil/2024/02/01/signature-of-equipment-russian-air-defense/) — Air defense system identification

## NATO eFP & Baltic Operations (Online)

- [NATO eFP Overview (NATO.int)](https://www.nato.int/cps/en/natohq/topics_136388.htm) — Official NATO page
- [SHAPE: NATO Forward Land Forces](https://shape.nato.int/efp) — Operational details
- [Allied Land Command: eFP](https://lc.nato.int/operations/enhanced-forward-presence-efp) — Landcom perspective
- [NATO eFP in the Baltics: Host & Framework Nation Nexus (PDF)](https://securityanddefence.pl/pdf-193734-124186?filename=NATO+enhanced+forward.pdf) — Academic analysis

## Classification

All documents in this folder are **UNCLASSIFIED** and publicly available. Do not add classified or export-controlled materials to this repository.
