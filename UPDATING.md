# Annual update checklist

The app's logic doesn't go stale, but its dollar figures do. Once a year (November, after the IRS publishes next year's numbers, is a good time), update the items below in `index.html`, then bump `DATA.year` and `DATA.reviewed`. If the app is opened in a year later than `DATA.year`, it shows a banner telling people some figures may be out of date.

Everything is in the block marked `ANNUAL UPDATE` near the top of the script.

| What | Where in index.html | Source |
|---|---|---|
| `DATA.year`, `DATA.reviewed` | `var DATA=` | — |
| 401(k)/403(b), 457(b), IRA, HSA family, dependent care FSA limits; 401(a)(17) pay cap and 415(c) total limit; Social Security wage base | `var LIM=` | IRS cost-of-living announcement (Oct/Nov); SSA wage base (Oct) |
| Federal brackets and standard deduction (joint, single, and married filing separately — `mfs`, used by the Loans tab) | `var FED=` | IRS Revenue Procedure for the coming tax year |
| SALT cap and phase-down, child tax credit | `taxCalc()` | IRS / current tax law |
| New Jersey brackets | `var NJBR=` | NJ Division of Taxation (change only when the law changes) |
| Role and specialty salaries | `var SPECS=` | AAPA Salary Report (spring), BLS OEWS (spring), AANP surveys |
| Federal student loan rates, RAP / IBR / PSLF rules | Student Loans tab text, `calcLoans()` | studentaid.gov (rates set each July) |
| NJ seller "mansion tax" tiers | `mansionRate()` | NJ Division of Taxation |
| NJ treatment of HSA contributions (taxed as of 2026; a bill to conform is pending) | HSA step text in `calcPlay()` | NJ Division of Taxation |
| Catch-up limits (`catch50`, `catch6063`) and the Roth-catch-up wage threshold ($150,000 in 2026, in the `catch-hint` text and the Playbook step) | `var LIM=`, `catch-hint`, `calcPlay()` | IRS cost-of-living announcement (Oct/Nov) |
| Pre-retirement card facts: ACA subsidy rules (enhanced credits expired after 2025), Social Security ages, RMD ages; college costs (College Board averages, published each fall: all-in private ~$61k / in-state public ~$26k for 2025–26; selective private ~$90–105k, 16 schools over $100k for 2026–27 per Princeton Review/CNBC — also the `col-amt` default of $90k and its hint) and the NJ 529 deduction income limit | `calcPlay()` — `pb-pre` and `pb-col` text | healthcare.gov / Congress; ssa.gov; IRS; College Board Trends in College Pricing; NJ Division of Taxation |
| Fixed-costs card facts: Social Security max benefit at 67 (~$45–50k/yr; $4,152/mo max at FRA in 2026), NJ property tax appeal deadline (April 1 in most towns) | `calcPlay()` — `pb-stuck` text | ssa.gov; NJ Division of Taxation |
| Gift tax annual exclusion and lifetime exemption (`giftExcl`, `giftLife`) | `var LIM=` | IRS cost-of-living announcement (Oct/Nov) |
| Medical-professional mortgage rate premium | `var PHYS=` | Quotes from lenders that offer these loans to PAs/NPs |
| Roth IRA income limits (`rothS`, `rothJ`) | `var LIM=` | IRS cost-of-living announcement (Oct/Nov) |
| RAP-only rule for anyone who borrowed on or after July 1, 2026 (`rapOnly()`, now = Student mode) and the RAP rate bands (`rapMo()`) | script, near `fpl150()` | studentaid.gov |
| PA/NP loan caps (professional-degree litigation) | Loans tab "What changed" text | studentaid.gov; AAPA / AANP advocacy pages |
| Ask AI tab: the guardrails and question menu (`AI_G`, `AI_Q`) and the savings-rate targets per goal (`AI_GOALS`) — reread them so they still match current rules (PSLF, Medicare, Social Security) | `var AI_G=`, `var AI_Q=`, `var AI_GOALS=` | studentaid.gov; ssa.gov; medicare.gov |
| Mortgage rate and property tax defaults | Rent vs Buy sliders `rvb-rate`, `rvb-tax` | Freddie Mac PMMS; NJ property tax averages |
| Childcare cost hint, living-cost estimates | `daymo` slider hint, `var EST=` | Local daycare rates; household spending |

After editing: open the app, check every tab for errors, and spot-check one known case (e.g. PA, all specialties $140k, single, age 27, 1 year of school left, $140k loans on PSLF, renting $2,200/mo → room to save about 20%, a small shortfall for the Roth IRA).
