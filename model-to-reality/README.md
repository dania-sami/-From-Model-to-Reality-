# From Model to Reality

**A runnable human-centred transport decision prototype.**

## Start in under one minute

1. Unzip the folder.
2. Open `index.html` in Chrome, Edge, Firefox, or Safari.
3. Follow the six stages: Challenge → Engineering model → Listen to people → Evidence translation → Implementation gates → Decision room.

No installation, API key, account, or backend required. The app works offline except for optional Google Fonts (it falls back to system fonts).

For local development you can also run `python -m http.server 8000` in this folder and visit `http://localhost:8000`.

## What is actually functional

- A parameterized, deterministic calculation model (daytime/evening service frequency, critical connection protection)
- Live cost, waiting-time, distance and missed-connection estimates
- Four scripted stakeholder interviews, each with three selectable questions
- Capture of stakeholder constraints into a persistent evidence log
- Stakeholder to requirement traceability with model changing constraints
- Side by side pre and post consultation calculation comparison
- Nine scenario sensitivity sweep over cost and demand assumptions
- Six implementation governance gates with owner/source notes and evidence status
- Six implementation and policy readiness questions
- Three decision pathways and quantitative comparisons
- A dynamically generated decision memo, downloadable as standalone HTML or printable to PDF
- Local browser persistence and reset
- Responsive layout

## Scientific integrity / important limitations

This is **not** a real transport forecast. The corridor, ridership, cost factors, missed-connection formula, personas and statements are entirely synthetic and illustrative. No real interviews were conducted. Policy checklist items are **questions to investigate**, not verified legal requirements. The scripted interviews are intentionally not marketed as AI or actual stakeholder evidence. The implementation is transparent and inspectable in `app.js`.

### Model assumptions

- Hypothetical 12 km corridor, 1,200 daily boardings (940 daytime, 260 evening)
- Baseline daytime and evening headway: 15 minutes
- Average random-arrival wait: headway / 2
- Daily service trip proxy: `48 + round(240 / daytimeHeadway) + round(180 / eveningHeadway)`
- Vehicle distance: `tripProxy × 12 km`
- Operating cost: `vehicleDistance × €6.50 / km`
- Vehicle emission proxy: `vehicleDistance × 0.9` (not surfaced as a validated emission figure)
- Missed critical connections proxy: `round(8 + max(0,(eveningHeadway - 15)/15) × 26 × (1 - protection × 0.55))`
- Weighted wait: `(940 × daytimeHeadway/2 + 260 × eveningHeadway/2)/1200`

These are teaching assumptions, not calibrated models. Avoid claiming causal inference or empirical accuracy.

## Next research steps

1. Define a real corridor and access permission for GTFS schedule and ridership data.
2. Validate the calculation engine against observed journeys and disruptions.
3. Conduct ethically appropriate real stakeholder interviews and document recruitment, consent and analysis.
4. Check applicable Swedish and regional legal, policy and procurement requirements with primary sources.
5. Co-design evaluation criteria with relevant passengers, operators and decision-makers.

## Files

- `index.html` — application shell
- `styles.css` — responsive interface
- `app.js` — model, stakeholder interaction, policy, decision memo and persistence
- `README.md` — setup, assumptions and limitations

Built as a portfolio research concept inspired by the challenge of connecting quantitative modelling, qualitative needs and implementation policy. It is independent and not affiliated with ResPT, SEI or any transport authority.

## V2 research workflow

The new **Evidence translation** stage converts fictional stakeholder concerns into explicit choices. Choosing critical connection protection or evening service preservation changes model inputs and recalculates results. The **Implementation gates** stage requires documenting owners, sources and evidence status, rather than treating checkbox completion as compliance. The exported decision memo includes both traceability and gate status.

All statements are illustrative. A user marking a gate verified is not external verification. The sensitivity sweep is a deterministic assumption test, not uncertainty quantification from empirical data.
