# Toxic Chemical Explorer

An interactive reference tool for exploring toxic chemicals and elements — their health hazards, GreenScreen benchmarks, manufacturer accountability data, legislation tracking, safer alternatives, and California Safe Cosmetics Program (CSCP) product counts.

## What it does

Search any of **206 chemicals and elements** by name, CAS number, or chemical class. Each entry includes:

- **Health & ecological hazards** with severity pips (1–5) across cancer, neurotoxicity, endocrine disruption, reproductive harm, persistence, and more
- **GreenScreen benchmark ratings** — BM-1 (Avoid) through BM-4 (Prefer) with color-coded pip indicators
- **Key manufacturers & polluters** — named companies with facility locations, enforcement history, and settlement amounts (80 entries)
- **Legislation tracking** — passed laws and proposed bills at federal, state, and international levels, with US + EU map visualization
- **Regulatory badges** — WA Safer Products for Washington, Toxic-Free Cosmetics Act, WA PBT rule, and CA Safe Cosmetics Program coverage
- **Safer alternatives** — specific alternatives by product context, sourced from WA Ecology Regulatory Determinations (35 entries)
- **Product status coding** — color-coded product chips: red (banned), orange (partially banned), yellow (abandoned by industry), white (active use)
- **CSCP product counts** — number of cosmetic products reporting each chemical to the California Safe Cosmetics Program
- **System dark mode** — automatically follows OS light/dark preference
- **Related chemicals** — clickable navigation between parent, child, and related entries

## Repository structure

```
index.html      — The UI application (~70KB). Loads chemicals.js, renders the interface.
chemicals.js    — The chemical database (~500KB). All 206 entries + alias lookup table.
README.md       — This file.
```

**The data and the UI are intentionally separated.** `chemicals.js` is a standalone JavaScript file that exposes `window.CURATED_DB` and `window.ALIASES`. It can be loaded by any future web application, exported to JSON, or migrated to a database without touching the UI code.

## Database coverage

**206 total entries** across:

- **71 curated chemicals** — TFF Toxic Chemicals page, WA Safer Products Cycles 1/1.5/2, WA Toxic-Free Cosmetics Act, WA PBT Rule, Stockholm Convention POPs, GreenScreen BM-1 chemicals, WHO acute pesticides, EWG dietary pesticides
- **110 periodic table elements** — all Z=1–118; 8 route via aliases to existing entries (Hg→heavy metals, As→heavy metals, Cr→hexavalent chromium, Pb→lead, Cd→cadmium, Sn→organotins, Sb→antimony, F→PFAS)
- **12 plastics** — overview, polyethylene, polypropylene, polystyrene, PET, polyurethane, polycarbonate, nylon, microplastics, ABS, bioplastics/PLA (plus PVC in the original 71)
- **5 EDCs** — perchlorate, diethylstilbestrol (DES), vinclozolin, phytoestrogens, UV filters (oxybenzone/octinoxate)
- **8 CSCP/TFF chemicals** — melamine, cyanuric acid, carbon black, toluene, coal tar, retinyl palmitate, ethanolamines (DEA/TEA/MEA), PEG compounds

## Data sources

- [WA Ecology Safer Products Cycle 1](https://apps.ecology.wa.gov/publications/documents/2204018.pdf) — Pub. 22-04-018
- [WA Ecology Safer Products Cycle 1.5](https://apps.ecology.wa.gov/publications/documents/2404024.pdf) — Pub. 24-04-024
- [TFF Breast Milk Study 2026](https://toxicfreefuture.org/research/endocrine-disrupting-plastic-chemicals-in-breast-milk/) — Nature journal, peer-reviewed
- [CA Safe Cosmetics Program (CSCP)](https://cscpsearch.cdph.ca.gov/search/publicsearch) — CDPH open data
- [Endocrine Society Common EDCs](https://www.endocrine.org/topics/edc/what-edcs-are/common-edcs)
- [GreenScreen for Safer Chemicals](https://www.greenscreenchemicals.org/)
- [Safer States Bill Tracker](https://www.saferstates.org/bill-tracker/)
- [EPA TRI Toxics Tracker](https://edap.epa.gov/public/extensions/TRIToxicsTracker/TRIToxicsTracker.html)
- [EJScreen (preserved)](https://pedp-ejscreen.azurewebsites.net/)

## Deployment

**GitHub Pages** — single directory deployment, no build step required.

1. Go to repository **Settings → Pages**
2. Source: Deploy from a branch → main → / (root)
3. Save — site deploys at `https://[username].github.io/toxic-chemical-explorer/`

Both `index.html` and `chemicals.js` must be in the same directory for the browser to load the data file.

## Updating the database

The database lives in `chemicals.js`. Each chemical entry follows this schema:

```javascript
"entry-key": {
  name: "Chemical Name",
  aka: ["Alias 1", "CAS number"],
  cas: "000-00-0",
  chemClass: { name: "Class name", def: "Definition" },
  desc: "Full description paragraph",
  formula: "C2H4",
  molWeight: "28.05",
  toxicity: [{ label: "Cancer", val: "Description of cancer hazard" }],
  gs: { bm: 1, label: "Benchmark 1 — Avoid", detail: "GreenScreen rationale" },
  parents: [], children: [],
  products: ["Product A", { name: "Product B", status: "banned", note: "Banned in 2016" }],
  func: "What this chemical is used for",
  links: [{ t: "Link title", u: "https://..." }],
  // Optional fields:
  manufacturers: [{ name: "Company", note: "Context" }],
  legislation: [{ st: "US", bill: "TSCA", status: "passed", title: "Description" }],
  saferAlternatives: [{ context: "Use case", alt: "Alternative", note: "Details" }],
  altSource: "Source citation",
  cscpData: { count: 1200, note: "Source note", categories: ["Hair care"], searchUrl: "https://..." },
  spwa: "Cycle 1",  // WA Safer Products coverage
  tfca: true,       // WA Toxic-Free Cosmetics Act
  waPBT: true,      // WA PBT Rule
}
```

**Product status values:** `banned`, `partial`, `abandoned` (or omit for active use)

## Tech stack

- React 18.2.0 (CDN, no build step)
- Babel standalone 7.23.9 (in-browser JSX transform)
- IBM Plex font family (Google Fonts)
- GitHub Pages (static hosting)

No build system, no Node.js required, no package.json. The entire application is two files.
