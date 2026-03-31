# Toxic Chemical Explorer

An interactive reference tool for exploring toxic chemicals in products — their health hazards, GreenScreen benchmarks, manufacturer accountability data, and the legislation working to restrict them.

## What it does

Search any of **71 curated chemicals** by name, CAS number, or chemical class. Each entry includes:

- **Health & ecological hazards** with visual icons for cancer, neurotoxicity, endocrine disruption, reproductive harm, persistence, and more
- **GreenScreen benchmark ratings** from Clean Production Action's methodology
- **Key manufacturers & polluters** — named companies with facility locations, enforcement history, and settlement amounts
- **Legislation tracking** — passed laws and proposed bills at federal and state levels, with links to Safer States bill tracker
- **Regulatory badges** — WA Safer Products for Washington, Toxic-Free Cosmetics Act, and PBT rule coverage
- **Related chemicals** — clickable navigation between parent, child, and related chemical entries
- **External reference links** — EPA, ATSDR, IARC, and other authoritative sources
- **EPA TRI Toxics Tracker** and **EJScreen** links for facility-level pollution data

For chemicals not in the curated database, an AI-powered fallback (requires Claude API access) researches the chemical and returns structured data.

## Chemical coverage

The database covers chemicals across major regulatory frameworks:

- **TFF Toxic Chemicals page** — all listed chemicals
- **WA Safer Products for Washington** — Cycles 1, 1.5, and 2
- **WA Toxic-Free Cosmetics Act** — all 25+ restricted chemicals
- **WA PBT Rule / Chemical Action Plans** — all covered chemicals
- **Stockholm Convention POPs** — new listings through 2025 (MCCPs, LC-PFCAs, Dechlorane Plus, UV-328, etc.)
- **GreenScreen BM-1 chemicals** — highest-concern chemicals
- **WHO acute pesticide intoxication** — key pesticides
- **EWG dietary pesticide exposure study** — malathion, chlormequat, dietary fungicides

## Data sources

- [Toxic-Free Future](https://toxicfreefuture.org/) — toxic chemicals information
- [GreenScreen for Safer Chemicals](https://www.greenscreenchemicals.org/) — benchmark methodology
- [Safer States Bill Tracker](https://www.saferstates.org/bill-tracker/) — state legislation
- [WA Dept. of Ecology](https://ecology.wa.gov/) — Safer Products for Washington, Toxic-Free Cosmetics Act
- [EPA TRI Toxics Tracker](https://edap.epa.gov/public/extensions/TRIToxicsTracker/TRIToxicsTracker.html) — facility pollution data
- [EJScreen (preserved)](https://pedp-ejscreen.azurewebsites.net/) — environmental justice mapping
- [Stockholm Convention](https://www.pops.int/) — persistent organic pollutants
- [USDA Pesticide Data Program](https://www.ams.usda.gov/datasets/pdp) — produce pesticide residues
- [EWG/Temkin et al. 2025](https://doi.org/10.1016/j.ijheh.2025.114654) — dietary pesticide exposure study

## Tech stack

Single-file React application. No build system required.

- React 18 (loaded from CDN)
- Babel standalone (for JSX transformation in-browser)
- Google Fonts (Literata + DM Sans)
- All data embedded — no external API calls needed for curated chemicals

## License

This tool is provided for educational and advocacy purposes. Chemical data is compiled from public sources and should be verified with authoritative references for regulatory or legal use.
