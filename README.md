# What local nonprofit newsrooms raise from the counties they sit in

Data behind *The Money Is Local. The Ask Isn't.* (Backstory & Strategy, October 2026).

## What's here

`nonprofit-newsroom-contributions-by-county.csv` — one row per nonprofit news organization (93 rows), with its
reported contributions, its home county, the households in the place it serves, and three county-level denominators.

| column | meaning |
|---|---|
| `outlet`, `legal_name` | Outlet as commonly known, and the name on its IRS filing |
| `scope` | Local, Regional or Statewide, as listed in the Institute for Nonprofit News member directory |
| `state`, `fips` | Headquarters state and county FIPS code (from the organization's IRS mailing address) |
| `latest_year`, `latest_contrib` | Most recent filing year with financials, and total contributions and grants (Form 990 Part VIII line 1h) |
| `prior_year`, `prior_contrib` | The filing before it, where one exists |
| `avg2_contrib` | Average of the two (or the latest alone where only one exists) |
| `hh` | County households, ACS 2020–2024 five-year estimate |
| `service_area_hh` | Households in the place the outlet actually serves: the county where it covers the county, or the city or town where it covers a defined place smaller than its county (ACS 2019–2023 place estimates). Filled for the 52 local outlets considered; blank for rows excluded on other grounds. 25 outlets have a service area smaller than their county; see the list below |
| `pool` | Grants paid by private foundations based in the county, IRS SOI 990-PF extract (program year 2024), after removing pharmaceutical patient-assistance programs and one double-counted pass-through trust, and capping any single foundation at $100M |
| `indiv` | Itemized charitable deductions claimed by county residents, IRS SOI county file, tax year 2023 |
| `per_hh` | `avg2_contrib / hh` (county denominator) |
| `per_hh_service` | `avg2_contrib / service_area_hh` — the per-household figure used in the piece |
| `share_pool` | `avg2_contrib / pool`, as a proportion |
| `share_pool_ind` | `avg2_contrib / (pool + indiv)`, as a proportion |
| `in_analysis` | `yes` for the 40 local outlets the piece's figures are computed on |
| `exclusion_reason` | Why a row is not in the 40: statewide scope, street paper, public media, multi-city network, magazine, civic-media organization, or a service area under 25,000 households (12 outlets; the piece discusses them separately) |

Where a county hosts more than one outlet in the analysis, the piece also reports county-level sums; those are
computed from these rows, not stored separately.

## Service-area assignments

Where an outlet covers a city or town rather than its whole county, `service_area_hh` uses that place's households.
The 25 reassignments (county households → service-area households):

| outlet | service area | county hh | service-area hh |
|---|---|---|---|
| Block Club Chicago, Chicago Reader, Injustice Watch, South Side Weekly, Borderless Magazine | Chicago city | 2,100,230 | 1,146,547 |
| Evanston RoundTable | Evanston city | 2,100,230 | 31,387 |
| City Limits | New York City (five boroughs) | 778,281 | 3,313,316 |
| Berkeleyside and The Oaklandside | Berkeley + Oakland | 598,246 | 219,941 |
| Outlier Media | Detroit city | 700,591 | 253,207 |
| Fort Worth Report | Fort Worth city | 782,419 | 334,230 |
| The New Bedford Light | New Bedford city | 233,825 | 42,233 |
| New Haven Independent | New Haven city | 230,673 | 53,424 |
| South Seattle Emerald | Seattle city | 941,054 | 353,019 |
| San Jose Spotlight | San José city | 659,353 | 326,767 |
| Canopy Atlanta, Atlanta Civic Circle | Atlanta city | 462,481 | 231,504 |
| The Land | Cleveland city | 554,551 | 168,652 |
| Austin Monitor | Austin city | 583,747 | 440,294 |
| Boulder Reporting Lab | Boulder city | 137,008 | 43,825 |
| Lexington Observer | Lexington town | 634,215 | 12,337 |
| Montclair Local | Montclair township | 319,788 | 15,118 |
| The Highlands Current | Philipstown + Beacon | 35,545 | 10,198 |
| Gig Harbor Now | Gig Harbor area | 351,330 | 22,847 |
| The Daily Catch | Red Hook + Rhinebeck | 116,275 | 7,589 |
| Ipswich Local News | Ipswich town | 313,147 | 5,757 |

Chicago's neighborhood outlets are assigned the whole city, which overstates their denominators; the piece says so.

## Versions

- v2 (Oct 27, 2026): added `service_area_hh` and `per_hh_service`; `in_analysis` now marks the 40 outlets with service areas of 25,000+ households (was 46 on county households); 12 smaller-service-area outlets carry their own exclusion reason. County-level columns unchanged.
- v1 (Oct 23, 2026): initial release.

## Sources

- Organization list: Institute for Nonprofit News member directory (findyournews.org), U.S. members with local, regional or statewide scope, October 2026.
- Financials: IRS Form 990 as published by ProPublica Nonprofit Explorer. Only organizations filing a full 990 or 990-EZ with financials appear; 990-N (postcard) filers carry no financial data and are absent.
- Households: U.S. Census Bureau, American Community Survey 2020–2024.
- Foundation pool: IRS Statistics of Income, Form 990-PF annual extract, matched to county through the filer's address in the Exempt Organizations Business Master File and the Census 2010 ZCTA-to-county relationship file.
- Individual giving: IRS Statistics of Income, county data, tax year 2023.

## What this can't tell you

- Line 1h includes every contribution an organization received, including national foundation grants, government grants and bequests, so the capture figures are upper bounds on *local* giving.
- Community foundations and donor-advised funds are public charities and do not file 990-PF, so `pool` understates local institutional giving.
- The county is the one the organization's mailing address sits in; the service area is the author's assignment of the place the outlet covers.
- Fiscally sponsored outlets file no 990 of their own; their contributions appear on the sponsor's return and they are absent here.
- A multi-year grant is booked in the year it is pledged, so year-over-year swings partly reflect accounting.
- This is a census of organizations that existed and filed; closed outlets are not in it.

## License

Data: public domain (U.S. government sources) with arithmetic added. Please cite the piece if you use the table.
