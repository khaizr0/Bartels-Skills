---
name: bartels-boq-review
description: >-
  Review construction / fit-out BOQs (bill of quantities), contractor
  quotations, cost estimates and variation orders for BARTELS sites,
  benchmarking every line against the library of past BARTELS BOQs. Use whenever
  Kasper shares a BOQ, a contractor price, a fit-out budget, a cost breakdown
  per m², a variation/change order, or asks 'is this price fair', 'compare these
  contractors', or 'what did we pay last time', even if he does not say 'BOQ'.
  Also use to ingest a settled/final BOQ into the library. Kitchen equipment
  lines inside a BOQ hand off to kitchen-hardware-review.
---
# BARTELS BOQ Review

Purpose: stop BARTELS overpaying for fit-outs. Contractors in Vietnam and Thailand quote inconsistent scope, pad quantities, hide prelims and provisional sums, and reprice the same item differently per site. The only reliable defence is the chain's own history: every past BARTELS BOQ is a benchmark. This skill forces every new BOQ through that history before Kasper approves anything.

## Where the context lives
Two stores, both in Kasper's Google Drive. Never guess rates from memory; read these.

| Store | What | How to find |
|---|---|---|
| Folder `BARTELS BOQ Library` | Raw past BOQs, quotes, final accounts (xlsx, pdf, dwg exports). One subfolder per site, e.g. `TH01 Thonglor`, `VN01 Thao Dien`, `VN03 Xuan Dieu` | `Google_Drive__search_files` name contains "BARTELS BOQ Library"; list children |
| Sheet `[CLAUDE WORK FILE] - BOQ Rate Library` | Distilled unit rates, one row per item per site per date. Schema in `references/rate-library-schema.md` | Search Drive by exact title; create it from the schema if missing |

Rules for the stores:
- Read the Rate Library first (fast, structured). Open a raw BOQ in the folder only when a line is missing from the library or the library row looks wrong.
- After every review, append the new BOQ's lines to the Rate Library tagged `status = quoted`. When Kasper says a BOQ is agreed/final, update those rows to `status = final` and copy the file into the site subfolder. The library only gets more useful if it is fed every time.
- Files attached in the chat count as input; still check the Drive library for benchmarks.

## Workflow
1. Identify: site (code + name), contractor, BOQ date, revision, currency, VAT basis (incl/excl, rate), gross floor area m² (pull from property-manager; never guess area).
2. Extract every line: section, item code, description (VN/TH + EN), unit, qty, unit rate ex-VAT, amount. Keep the contractor's own numbering so feedback is traceable.
3. Recompute: every line qty × rate, section subtotals, prelims %, contingency %, VAT amount and rate actually applied, grand total. Never trust the printed total.
4. Normalise and benchmark: map each line to the Rate Library item key (see schema). For each, show library low / median / high and the delta %. Flag per the thresholds below.
5. Scope audit: run Checklists A to F. Identify missing scope that will arrive later as a variation.
6. Quantity audit: check headline quantities against the floor area and drawings (floor finish m² vs GFA, ceiling m², wall paint m² ≈ perimeter × height × 2 less openings, lighting points vs layout, power points vs equipment list). Anything > 15% over the geometric estimate is ⚠.
7. If two or more contractors: align by normalised item, compare per unit ex-VAT, show scope gaps per contractor in their own column. Never compare a total against a total when the scopes differ.
8. Output per the format below, then a question list for the contractor.
9. Feed the Rate Library.

## Flag thresholds vs library median (per unit, same unit, same currency)
| Delta | Flag |
|---|---|
| > +25% | 💀 overpriced, ask for justification or re-quote |
| +10% to +25% | ⚠ probe, may be spec or site-driven |
| -10% to +10% | ✅ in line |
| < -10% | ❓ suspiciously cheap, check spec/qty/exclusions |
| No library match | ❓ new item, benchmark externally if material (> 1% of total) |
Material items (top 20 lines by amount, usually ~80% of value) get a row each; the long tail is summarised.

## Checklist A: commercial terms
- Payment schedule: advance %, stage milestones, retention (BARTELS standard: 10% retention until defects liability ends, 5% min). 50%+ advance is 💀.
- Defects liability period (12 months standard), warranty on waterproofing (5 years+), MEP, joinery.
- Programme: start, completion, liquidated damages per day. Check against the site's rent-free / fit-out window from property-manager; a programme that ends after rent starts is ‼.
- Variations: unit rates fixed for additions and omissions, written approval required, no "as instructed on site" pricing.
- Validity, currency, escalation clause, who bears material price rises.
- VAT: rate stated vs rate calculated (Vietnam 8% vs 10%; Thailand 7%). Invoicing entity (CONG TY TNHH BARTELS or the Thai entity), red/tax invoice per stage.
- Insurance: contractor all-risks, third party, workers. Permits and landlord fit-out deposit responsibility.

## Checklist B: prelims, provisional and lump sums
- Prelims (site management, hoarding, scaffolding, temp power/water, cleaning, waste, landlord fees): expect 8 to 15% of works. Above that ⚠, and check items are not also inside sections.
- Provisional sums and PC rates: list every one; each is an unpriced risk. Ask for firm prices or a cap.
- Lump sums without qty/unit: 💀 for anything > 1% of total. Demand breakdown.
- Contingency: BARTELS carries its own; a contractor contingency on top is double counting.
- Overheads and profit shown separately or embedded: state which.

## Checklist C: scope completeness (fit-out)
Walk the standard BARTELS fit-out scope and mark present / missing / excluded:
- Demolition and disposal, protection of landlord elements.
- Structural: openings, steel for mezzanines or signage, floor levelling.
- Waterproofing: wet kitchen, toilets, outdoor terrace, with test.
- Floor finishes, skirting, thresholds; wall finishes, tiling behind kitchen lines; ceilings and bulkheads.
- Joinery and FF&E: counter, display, back bar, seating, tables, shelving (specify material, finish, hardware brand).
- MEP electrical: DB, 3-phase supply upgrade (EVN application), cabling, lighting (fittings supplied by whom), sockets by equipment list, emergency lighting.
- MEP mechanical: AC (brand, kW per unit, condensers location), kitchen extraction hood, duct, fan, make-up air, fresh air, grease filter, ecology unit if landlord requires.
- MEP plumbing: hot and cold water, grease trap (size per ATTP / landlord), floor drains, booster pump, water filtration for coffee and ice.
- Gas: LPG line, cabinet, detectors, if any.
- Fire: sprinkler relocation, smoke detectors, extinguishers, fire certificate (PCCC) liaison in Vietnam.
- Signage, facade, awning, outdoor furniture, lighting.
- IT and low voltage: data points, CCTV, speakers, Wi-Fi, POS cabling.
- Soft: as-built drawings, test and commissioning, landlord handover, authority submissions.
Anything missing from a "turnkey" quote is a future variation and gets ‼.

## Checklist D: spec integrity
- Material and brand named per line (tile model, paint brand/grade, SS304 vs SS201, plywood grade, laminate brand, AC brand and model). "Equivalent" or "or similar" is ⚠; "to be confirmed" is ❓.
- Bilingual columns must agree (qty, unit, description).
- Unit mismatches: m vs m², set vs pcs, LS vs measurable. Unit rate changes between revisions of the same BOQ ‼.
- Copy-paste rates: identical rate for different specs across lines.
- Compare spec against BARTELS brand standard (bartels-interior-review holds the standard where defined; mark TO CONFIRM otherwise).

## Checklist E: quantity sanity
- Floor finish m² vs net floor area; ceiling m² vs net area; paint m² vs geometric estimate.
- Points: lighting, power, data vs the equipment list and furniture layout.
- AC total kW vs area (cafe front of house ~150 to 200 W/m² cooling in HCMC/Bangkok, kitchen higher). Over-specced AC is cost; under-specced is complaints.
- Joinery linear metres vs plan.
- Waste and disposal volumes vs demolition scope.

## Checklist F: comparison hygiene (2+ contractors)
- Same revision of drawings issued to all. Same VAT basis. Same handover state assumed.
- Exclusions table per contractor side by side.
- Normalise lump sums into the section they belong to before comparing sections.
- Lowest total is rarely lowest final cost; estimate "likely final" = total + priced missing scope + provisional sums at library median.

## Per m² benchmarks
Keep live in the Rate Library `Summary` tab (total fit-out cost per m² GFA by site, split FOH / BOH / MEP / joinery). Quote these to Kasper on every review as the first sanity check. Until seeded, mark ❓.

## Output format
Kasper's rules: tables not bullets, short titles, metric only, no em dashes, dates DD/MM/YY, VND in M with two decimals, THB in K.
Emoji key: 🔥 pro, 💀 con, ‼ critical, ❓ unknown/confirm, ⚠ risk/probe, ❌ false/debunked, ✅ verified, ℹ FYI.

1. Headline: site, contractor, BOQ date/rev, total ex/incl VAT, cost per m² vs library range, one-line verdict (Approve / Negotiate / Re-quote).
2. Table: commercial and structural issues (terms, prelims, provisional sums, programme, VAT).
3. Table: line benchmarks for material items (item, qty, rate, library median, delta %, flag, note).
4. Table: scope gaps (item, present/missing/excluded, estimated value from library).
5. Table: contractor comparison when 2+ (normalised section, each contractor, likely final).
6. Negotiation targets: top 5 asks with the VND/THB value of each.
7. Questions to the contractor, grouped Clarify / Terms / Add / Remove.
Keep it screenshot-friendly. If a Google Sheet is requested, title "[CLAUDE WORK FILE] - <site> BOQ review" with the standard header/body colours.

## Hand-offs
- Kitchen/bakery equipment lines: kitchen-hardware-review.
- Site areas, dates, landlord rules, fit-out windows: property-manager.
- Design/brand standard compliance: bartels-interior-review.

## Standing asks to every contractor
- Full measurable breakdown, no lump sums above 1% of total.
- Firm prices or caps on all provisional sums.
- Fixed unit rates for variations, additions and omissions.
- 10% retention through defects liability, staged payments tied to inspected milestones.
- VAT rate stated as applied, tax invoice per stage to the correct entity.
- Programme with completion date inside the rent-free window and LDs per day.
