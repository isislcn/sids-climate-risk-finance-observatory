# SIDS Climate-Disaster Risk Finance Tracker — Specification

**Status:** Draft for human review  
**Version:** 0.1  
**Coverage start:** 1 January 2020  
**Purpose:** Define the dataset, evidence rules, and minimum sortable/summarizable experience before populating an initiative inventory.

## 1. Product requirements

### Must have

1. Identify initiatives involving a UN-listed SIDS State or Associate Member, using UN-OHRLLS membership and region as the source of truth.
2. Include only initiatives with a documented climate-action or climate-disaster-risk connection and a documented financing/de-risking mechanism or relevant capacity-building component.
3. Capture the financing mechanism, qualifying year/date, SIDS region, MDBs/funds, private-sector/financial-company involvement, countries and country roles, initiative types, description, importance, population/community reach, funding timing/stage, financial scale, and three ranked links.
4. Permit sorting, filtering, and summary by each normalized field above.
5. Show evidence, source dates, and missingness/uncertainty without presenting unknown values as zero or confirmed facts.
6. Preserve funding stage and amount concept so announced, approved, committed, disbursed, guaranteed, insured, and paid-out values cannot be combined accidentally.

### Should have

- Parent/child links for facilities, programs, components, and subprojects.
- Search, export, and reproducible summary views.
- A correction log and record-level review status.
- Separate reported currency/amount from any converted USD amount.

### Out of scope for first release

- Financial auditing, impact evaluation, causal attribution, loss modeling, recommendations, or claiming comprehensiveness.
- Unverified individual-level data or personally identifiable beneficiary information.
- Automatically inferring North/South groupings, project impact, or missing financial values.

## 2. Unit of record and inclusion logic

The primary unit is a **publicly documented initiative** with a stable record ID. A program, facility, bond issuance, insurance cover, grant, project, or distinct financing window can each be an initiative if its scope and financing can be described without double-counting. Record the initiative's parent if it is a component. Avoid one record per press release.

A record qualifies when:

- at least one participating, beneficiary, covered, or implementing jurisdiction is included in the UN-OHRLLS SIDS roster (State or Associate Member);
- it has an evidenced climate action or climate-disaster-risk connection;
- financing/de-risking is documented, or capacity building is specifically directed toward enabling such finance; and
- the qualifying announcement, approval, commitment, financing, or implementation milestone is dated 2020-01-01 or later.

Record which event establishes date eligibility. The project may have started before 2020 if a qualifying funding or implementation milestone occurred in/after 2020; note this distinction. A data-collection date is not a qualifying project date.

## 3. Data model

Use linked/repeatable tables or equivalent structured fields. Do not flatten multiple countries, funders, mechanisms, funding events, or sources into a single unparseable text cell.

### 3.1 Initiative

| Field | Type / allowed values | Required | Meaning / evidence rule |
|---|---|---:|---|
| `initiative_id` | Stable text ID | Yes | Unique internal identifier; unchanged if display name changes. |
| `name` | Text | Yes | Source-backed initiative name; retain common acronym separately if useful. |
| `parent_initiative_id` | ID or null | No | Parent program/facility; use to identify nested records and avoid double counts. |
| `record_type` | Controlled: project, program, facility, instrument/issuance, insurance/cover, grant, other | Yes | What the record principally represents. |
| `summary` | Short text | Yes | Neutral, concise summary of documented purpose and financing. |
| `description` | Text | Yes | What is to be built, delivered, covered, or enabled, including location and components where sourced. |
| `importance` | Text | Yes | Documented rationale/problem or stated significance; attribute claims to source. Not an impact evaluation. |
| `climate_risk_link` | Multi-select + explanatory text | Yes | E.g. cyclone, flood, drought, sea-level rise, coastal erosion, heat, multi-hazard, general climate resilience, mitigation-only. Do not infer a hazard. |
| `status` | Controlled: proposed, announced, approved, committed, contracted, active, completed, cancelled, unknown | Yes | Best-supported current or as-of status. Preserve event history where statuses change. |
| `qualifying_event` | Controlled + date | Yes | 2020+ announcement/approval/commitment/funding/implementation event establishing inclusion. |
| `start_date`, `end_date` | Date or unknown | No | Project period, distinguish from funding event dates. |
| `sids_region` | Caribbean, Pacific, AIS, multi-region | Yes | Based on UN-OHRLLS roster; multi-region if more than one region. |
| `membership_basis` | State, Associate Member, both/mixed | Yes | Basis for SIDS inclusion. |
| `initiative_types` | Multi-select from taxonomy below | Yes | Documented intervention/activity and/or finance-purpose tags; identify primary and secondary where feasible. |
| `community_reach_summary` | Text | Yes | Short evidence-aware statement or “Not disclosed”. |
| `reach_disclosure_status` | disclosed, target only, estimate, not disclosed, conflicting | Yes | What kind of reach evidence exists. |
| `reach_value` | Number or null | No | Numeric only where source reports a count. |
| `reach_unit` | people, households, farmers, communities, facilities, other, not applicable | Conditional | Match source; do not convert unlike units. |
| `reach_geography` | Text or linked jurisdictions | Conditional | Where the count applies, if disclosed. |
| `reach_period` | Text/date range | No | Distinguish annual, cumulative, target horizon, or one-off reach. |
| `reach_evidence_type` | actual, target, estimated, exposed, insured/covered, unknown | Conditional | Do not call a target or exposed population an impacted population. |
| `importance_evidence_note` | Text | No | Attribution/caveat where the rationale is disputed or promotional. |
| `last_verified` | Date | Yes | Most recent date the record was checked against its sources. |
| `editorial_status` | research, needs review, reviewed, excluded | Yes | Workflow status, not project status. |
| `review_notes` | Text | No | Uncertainty, conflicting evidence, inclusion rationale, and known gaps. |

### 3.2 Financing mechanisms and funding events

An initiative can have multiple mechanisms and multiple funding events. Keep mechanism type separate from amount, source, and stage.

**Mechanism taxonomy (multi-select):**

- Grant / technical assistance
- Concessional loan / development loan
- Sovereign or sub-sovereign debt
- Green, blue, resilience, or sustainability bond
- Catastrophe bond / other capital-markets risk transfer
- Parametric or indemnity insurance / reinsurance
- Regional risk pool / pooled insurance
- Contingent credit / catastrophe deferred drawdown / pre-arranged credit
- Guarantee / credit enhancement / risk-sharing
- Equity / blended finance
- Budgetary/pre-arranged reserve or contingency financing
- Other (describe)
- Not disclosed

For each mechanism record: mechanism subtype/name, risk or funding function (risk transfer, risk retention, liquidity/pre-arranged response, investment capital, grant/TA, other), instrument/facility name, who bears/receives risk or funds if documented, and source(s). “Green bond” is a debt instrument; do not classify every climate loan as a bond.

For each **funding event**, capture:

| Field | Type / allowed values | Required |
|---|---|---:|
| `event_id` | Stable ID | Yes |
| `initiative_id` | Linked ID | Yes |
| `event_type` | announced, approved, committed, signed, effective, disbursed, payout, cancelled, repayment, other | Yes |
| `event_date` | Date or date precision (day/month/year/year-only) | Yes if sourced |
| `amount` | Decimal or unknown | Conditional |
| `currency` | ISO currency code or unknown | Conditional |
| `amount_concept` | Project cost, financing approved, commitment, disbursement, grant, loan, bond size, guarantee ceiling, insured coverage, payout, co-financing, mobilized/leveraged, other | Conditional |
| `contributor_or_provider` | Linked organization/country | No |
| `recipient_or_vehicle` | Text or linked country/entity | No |
| `amount_basis` | Single source, subtotal, total, maximum/ceiling, estimate, unknown | Conditional |
| `source_id` | Linked evidence | Conditional |
| `notes` | Text | No |

Never sum different amount concepts as if they were comparable. Retain original values. Any USD normalized field is derived and must specify FX source, conversion date, rate, and formula. Avoid counting both a parent envelope and its component allocations in the same total.

### 3.3 Countries and jurisdictions

Create a relationship for each jurisdiction and its role. Roles may include: SIDS beneficiary, covered/insured member, project location, implementing government, recipient, donor/contributor, guarantor, investor, other participant. One country can have multiple roles.

Required linked fields:

- country/jurisdiction name and stable identifier where available;
- UN SIDS membership status and region, with roster source and check date;
- role(s) in the initiative;
- Global North/Global South category only when assigned using a specified, versioned classification framework and source;
- classification source/version/date and any “unclassified/contested” value.

Global North/South is not a UN-OHRLLS SIDS-region field and has no single universally accepted country list. The dataset must not silently derive it from income, donor status, or SIDS status. Keep donor and beneficiary roles independent from North/South tags.

### 3.4 Organizations

Link organizations to initiatives and, where possible, funding events. Capture:

- canonical name, acronym, organization type (MDB, UN agency, climate/disaster fund, government, regional body, insurer/reinsurer, bank, investor, broker, private company/contractor, NGO, research entity, other);
- role(s): funder, co-financier, borrower/recipient, insurer, reinsurer, investor, guarantor, administrator, executing/implementing agency, technical-assistance provider, contractor, other;
- country/jurisdiction (if attributable);
- source(s) and evidence note.

Do not list a company as a financier merely because it implements a contract. “Involved private sector” means a named private-sector entity with an evidenced role; differentiate financial companies from other companies.

### 3.5 Initiative-type taxonomy

Allow multiple standardized tags; record a short rationale/source-backed detail when helpful. Support the user-requested tags:

- Adaptation
- Mitigation
- Capacity building
- Risk pooling
- Pre-arranged finance
- Agriculture / food security
- Sea wall / coastal protection
- Transportation
- Early warning system

Additional useful tags: disaster preparedness/response, resilient infrastructure, water/sanitation, energy, health, housing, ecosystem/nature-based solutions, fisheries/ocean, relocation, fiscal resilience, insurance, debt/climate finance, other. A mechanism such as risk pooling is not necessarily a physical project component; preserve separate mechanism and initiative-type fields.

### 3.6 Evidence and top links

For each source capture: `source_id`, title, publisher/author, URL, publication date (or unknown), source type, access date, archived/stable URL if available, and reliability note. Associate sources with the claims/fields they support.

Rank up to three **top relevant links**:

1. Primary project/facility or official announcement that establishes what the initiative is.
2. Primary financing disclosure or project document that supports mechanism, amount, and stage.
3. Primary implementation/reach source or credible independent reporting that adds material corroboration/context.

If fewer than three suitable sources exist, list fewer; never pad with irrelevant links. Prefer working primary links and verify access during research. A source may support more than one claim, but each key financial/date/reach claim needs traceable evidence.

## 4. Controlled values and data quality

- Missing values must be explicit: `Not disclosed`, `Not applicable`, `Unknown`, or `Conflicting sources`, as appropriate. Numeric zero means the source explicitly reports zero.
- Dates must retain precision; a year-only date must not be converted to an invented month or day.
- Preserve source wording and original amounts in research notes where normalization might alter meaning.
- Record “who said it” for population and impact claims; distinguish intended, targeted, reached, covered, exposed, and impacted individuals.
- Use the source's exact project or facility name, while maintaining a canonical display name and aliases for search.
- Store roles and multi-value data as linked rows or arrays—not comma-separated values that cannot be reliably filtered.
- Prefer primary institutional sources for financial facts and official roster membership. Use reputable journalism for context or corroboration, and label it as secondary.
- Deduplicate by instrument/project scope, not merely by similar name. Track aliases, parent-child relationships, and overlapping financial envelopes.
- Mark record confidence/review status at the claim or record level; do not imply independent audit.

## 5. Summaries and sorting

Every main requested parameter must be filterable or sortable, including:

- year (qualifying event and distinct funding-event dates);
- SIDS region and membership status;
- mechanism and instrument type;
- MDB/fund and private-sector organization/role;
- participating countries, roles, SIDS region, and sourced North/South classification;
- initiative-type tags;
- financing/project description and stated importance (searchable text);
- reach value, unit, evidence type, and disclosure status;
- funding stage/timing;
- reported amount, currency, and amount concept;
- top-source publisher and verification date.

Summary views may show counts by initiative, amount totals only when amount concepts/currencies are comparable, and reach totals only when units, periods, and evidence types are compatible. Each summary must display applied filters, date range, inclusion of missing values, unit/currency conventions, and overlap caveats. Do not publish a single grand “total funding” or “people impacted” number from incommensurate rows.

## 6. User-facing behavior

- An initiative row/detail page should label **reported facts**, **derived values**, and **editorial notes** distinctly.
- Each link opens with title, publisher, and date visible; external links should be checked on a schedule or before release.
- Filters should be combinable across facets, reset, and show their selected states. The current prototype allows one value per facet; multi-select within a facet remains a follow-on.
- Sorting on amounts must retain currency/amount concept context; default sort should not compare mixed currencies as numeric equivalents.
- A “not disclosed” filter/value must be distinct from an empty result.
- Exports must include IDs, definitions/codebook, source URLs, dates, and normalized categorical values.
- Do not collect personal data about beneficiaries. Aggregate counts only, with source and aggregation caveats.

The static prototype in `site/index.html` implements the review-stage catalogue, advanced filters, per-field sorting, category-count summaries, record details, and filtered CSV export. It currently contains only one research candidate, not a verified or comprehensive SIDS inventory. Summary charts count records by category; they do not sum money or beneficiaries. Before scaling the data, re-check the interface against populated records, adopted classification rules, and the acceptance criteria below.

## 7. Acceptance criteria

1. A reviewer can trace every initiative's eligibility, SIDS region/member status, qualifying date, mechanism, financing stage, amount, involved organization role, country role, and stated reach to sources or see an explicit missing/conflicting status.
2. User-requested tags are independently filterable; multiple tags on one record work.
3. User can sort/filter initiatives by every parameter in Section 5 and inspect supporting evidence.
4. A source that states “up to” a facility ceiling is not displayed as a disbursement; a target population is not displayed as actual impacted people.
5. A bond size, project total cost, approved finance, disbursement, guarantee amount, insured coverage, and payout remain distinguishable.
6. A regional initiative can link multiple countries and regions without duplicating the initiative; rollups do not double count its financial envelope.
7. Associate Members can be included and filtered separately from States; the exact UN roster source/check date is retained.
8. Global North/South labels identify their methodology/version, and unresolved classifications remain unclassified rather than guessed.
9. The top-links list contains no more than three relevant verified links and may contain fewer.
10. Summary totals disclose currency, unit, amount concept, reach evidence type, filters, and overlap/missing-data treatment.

## 8. Authoritative scope references

- [UN-OHRLLS: About Small Island Developing States](https://www.un.org/ohrlls/content/about-small-island-developing-states) — UN description of 39 States and 18 Associate Members, and the Caribbean, Pacific, and AIS regions.
- [UN-OHRLLS: List of SIDS](https://www.un.org/ohrlls/content/list-sids) — membership roster to consult and date-stamp.

These links establish the proposed eligibility framework; they do not themselves verify individual initiatives or funding.
