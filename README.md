# CivilWorks Atelier

A static engineering website (GitHub Pages ready): eleven interactive **studios** (sketch → engineering drawing, frame & beam, borehole & strata, CPT (cone penetration testing — SBT/SBTn charts, parameters, layering, CPT/SPT/Vs liquefaction with LPI/LSN/LDI, footing settlement, pile capacity, dissipation, AGS4/PDF/Excel), retaining wall, bridge, channel, road, onsite yard, estimating, construction forms — gallery at `studios.html`), five discipline wings (geotechnical, structural, bridges & flyovers, hydraulics, transportation) with 435+ calculations (including a temporary works & site section: crane lifts, outrigger mats, spreader beams, lifting lugs, pile lifting, Hiley driving, bored pile quantities, working platforms, batters, trench shoring and formwork pressure), a frame & beam analysis studio (SFD, BMD, axial force, deflection, influence lines, moving loads), a borehole & strata studio, 43 whole-structure estimators, an organised interactive lab of 231 demos, an **onsite yard** (animated, to-scale scenes of a crawler crane driving a precast pile, a rotary rig drilling and concreting a bored pile, and a crane lift against its load chart), **construction forms** (18 templates — RFI, site instruction, variation, transmittal, payment claim, ITP, NCR, pre-pour, driven and bored pile records, defects, SWMS, toolbox, permit to work, incident, plant pre-start, lift plan, site diary — with signatures, a numbered register, PDF, PNG and Excel), a journal, and demo accounts with Free and Pro plans.

## Studios
The newer studios share `assets/js/studio-kit.js` (layout, sliders, presets, checks, SVG/PNG/Excel export and a to-scale drawing kit with title block). Each studio is one file: `studio-bridge.js`, `studio-wall.js`, `studio-channel.js`, `studio-road.js`, plus `sketch-studio.js` (stroke recognition, snapping, live frame analysis via `frame-core.js`, DXF export, hand-off to the Frame studio). Wing and studio illustrations are drawn live by `assets/js/wing-art.js` and follow the light/dark theme.

## Branding
The logo lives in `assets/img/` (`logo-mark*` for the navigation, `logo-full*` for the home page, `favicon.png`; `-light` variants for dark mode) and as data URIs in `assets/js/logo-data.js` for drawings and PDFs. Company name on forms is set per project in the forms page's *Project settings*.

## Publish
Push the folder to a GitHub repository and enable **Settings → Pages → Deploy from branch (main, / root)**. No build step is needed.

## Edit pages
Shared header, navigation and footer are generated: edit `tools/build_pages.py` (and the page sources in `tools/src/`), then run `python3 tools/build_pages.py`. Rebuild the search index with `python3 tools/build_search_index.py` (needs Playwright).

## Accounts and subscriptions
`assets/js/auth-config.js` holds plans, prices, the free download allowance and which buttons are gated. The current backend is **local demo accounts** (stored in the visitor's browser, SHA-256 hashed passwords, no payments). To go live, implement the `store` adapter in `assets/js/auth.js` against Supabase or Firebase Auth and add checkout links (e.g. Stripe) in `auth-config.js`. Note that client-side gating alone cannot protect paid features; once payments are real, generate Pro exports server-side or verify the subscription with your backend.

## Tests
`node tests/frame.test.js`, `node tests/strata.test.js`, `node tests/calc.test.js`, `node tests/ft.test.js`, `node tests/v10.test.js`, `node tests/forms.test.js`, `node tests/cpt.test.js`.

All calculations are for preliminary and educational use and follow Australian Standards conventions; have designs checked by a qualified engineer.
