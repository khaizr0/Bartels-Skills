# BOQ Rate Library schema

Google Sheet title: `[CLAUDE WORK FILE] - BOQ Rate Library`
Styling: header row white text on dark blue 3; body rows black text on light blue 3.

## Tab `Rates` (one row per BOQ line, per site, per quote)
| Column | Type | Notes |
|---|---|---|
| item_key | text | Normalised key, snake_case, e.g. `floor_tile_600x600_porcelain`, `ac_split_wall_2.5kw`, `paint_wall_dulux_interior`, `grease_trap_ss304_500l`. Reuse existing keys before inventing one. |
| section | text | Prelims / Demolition / Structural / Waterproofing / Floor / Wall / Ceiling / Joinery / Electrical / Mechanical / Plumbing / Gas / Fire / Signage / IT / Soft |
| description_original | text | Contractor's wording, original language |
| spec | text | Brand, model, grade, size |
| unit | text | m, m², m³, pcs, set, LS, point |
| unit_rate_ex_vat | number | Local currency |
| currency | text | VND or THB |
| qty | number | |
| amount_ex_vat | number | qty × rate |
| site_code | text | TH01 to TH10, VN01+, CK01 for central kitchen |
| site_name | text | |
| contractor | text | |
| boq_date | date | DD/MM/YY |
| revision | text | R0, R1, final account |
| status | text | quoted / agreed / final |
| source_file | text | Drive file name |
| notes | text | Exclusions, oddities |

## Tab `Summary` (one row per site per final BOQ)
| Column | Notes |
|---|---|
| site_code, site_name, contractor, final_date | |
| gfa_m2 | From property-manager |
| total_ex_vat, currency | |
| per_m2 | total / GFA |
| prelims_pct, joinery_pct, mep_pct, finishes_pct | share of total |
| programme_weeks | agreed vs actual |
| variation_pct | variations / original contract |

## Tab `Contractors`
| Column | Notes |
|---|---|
| contractor, country, contact | |
| sites_done | |
| typical_advance_pct, retention_pct | |
| on_time | yes / no / partial |
| notes | quality, disputes, would-use-again |

## Normalisation rules
- Convert everything to ex-VAT before storing.
- Keep the original unit; add a converted row only when needed for comparison (e.g. LS split into measurable).
- Same item, different spec = different item_key. Spec drives price.
- When a library median is quoted to Kasper, state the number of rows behind it; one row is not a benchmark, mark ❓.
