# What local nonprofit newsrooms raise from the counties they sit in

Data behind *The Money Is Local. The Ask Isn't.* (Backstory & Strategy, October 2026).

## What's here

`nonprofit-newsroom-contributions-by-county.csv` — one row per nonprofit news organization (93 rows), with its
reported contributions, its home county, and three county-level denominators.

| column | meaning |
|---|---|
| `outlet`, `legal_name` | Outlet as commonly known, and the name on its IRS filing |
| `scope` | Local, Regional or Statewide, as listed in the Institute for Nonprofit News member directory |
| `state`, `fips` | Headquarters state and county FIPS code (from the organization's IRS mailing address) |
| `latest_year`, `latest_contrib` | Most recent filing year with financials, and total contributions and grants (Form 990 Part VIII line 1h) |
| `prior_year`, `prior_contrib` | The filing before it, where one exists |
| `avg2_contrib` | Average of the two (or the latest alone where only one exists) |
| `hh` | County households, ACS 2020–2024 five-year estimate |
| `pool` | Grants paid by private foundations based in the county, IRS SOI 990-PF extract (program year 2024), after removing pharmaceutical patient-assistance programs and one double-counted pass-through trust, and capping any single foundation at $100M |
| `indiv` | Itemized charitable deductions claimed by county residents, IRS SOI county file, tax year 2023 |
| `per_hh` | `avg2_contrib / hh` |
| `share_pool` | `avg2_contrib / pool`, as a proportion |
| `share_pool_ind` | `avg2_contrib / (pool + indiv)`, as a proportion |
| `in_analysis` | `yes` for the 46 local outlets the piece's figures are computed on |
| `exclusion_reason` | Why a row is not in the 46: statewide scope, street paper, public media, multi-city network, magazine, civic-media organization, or a county under 25,000 households |

Where a county hosts more than one outlet in the analysis, the piece also reports county-level sums; those are
computed from these rows, not stored separately.

## Sources

- Organization list: Institute for Nonprofit News member directory (findyournews.org), U.S. members with local, regional or statewide scope, October 2026.
- Financials: IRS Form 990 as published by ProPublica Nonprofit Explorer. Only organizations filing a full 990 or 990-EZ with financials appear; 990-N (postcard) filers carry no financial data and are absent.
- Households: U.S. Census Bureau, American Community Survey 2020–2024.
- Foundation pool: IRS Statistics of Income, Form 990-PF annual extract, matched to county through the filer's address in the Exempt Organizations Business Master File and the Census 2010 ZCTA-to-county relationship file.
- Individual giving: IRS Statistics of Income, county data, tax year 2023.

## What this can't tell you

- Line 1h includes every contribution an organization received, including national foundation grants, government grants and bequests, so the capture figures are upper bounds on *local* giving.
- Community foundations and donor-advised funds are public charities and do not file 990-PF, so `pool` understates local institutional giving.
- The county is the one the organization's mailing address sits in.
- Fiscally sponsored outlets file no 990 of their own; their contributions appear on the sponsor's return and they are absent here.
- A multi-year grant is booked in the year it is pledged, so year-over-year swings partly reflect accounting.
- This is a census of organizations that existed and filed; closed outlets are not in it.

## License

Data: public domain (U.S. government sources) with arithmetic added. Please cite the piece if you use the table.
