# SIDS Climate-Disaster Risk Finance Tracker — Backlog

**Status:** Draft for human review  
**Purpose:** Sequence the work from an agreed research framework to a reviewable, evidence-linked inventory. This backlog is intentionally a proposed work plan, not a claim that the inventory is complete.

## Prototype checkpoint

A static GitHub Pages dashboard scaffold now exists in `site/index.html`, with filters, sorting, category-count summaries, detail/source views, filtered CSV export, and a separate JSON codebook export. It contains one **research candidate** whose named SIDS beneficiary eligibility remains unverified; it is not a confirmed initiative in the SIDS inventory. P0 scope approval, source verification, data collection, and review remain open. UI coverage with multiple verified records and multi-select within facets is still needed.

## Prioritization

- **P0 — Required for trustworthy first release**
- **P1 — Important follow-on**
- **P2 — Optional enhancement**

## P0 — Agree scope and data conventions

### 1. Approve UN SIDS eligibility
- Confirm that both the 39 UN-listed States and 18 Associate Members are in scope, or narrow to States only.
- Establish the membership roster snapshot date and link for the working dataset.
- Store region exactly as UN-OHRLLS assigns it: Caribbean, Pacific, or Atlantic, Indian Ocean and South China Sea (AIS).
- **Done when:** the roster is available as a controlled lookup and an editor can explain inclusion for any covered jurisdiction.

### 2. Approve definition of qualifying climate-disaster initiative
- Confirm whether mitigation-only projects qualify absent an explicit disaster-risk link.
- Adopt the inclusion test and the 2020+ qualifying-event rule from the specification.
- Decide treatment of project activity that predates 2020 but receives a post-2020 commitment or has a new funding event.
- **Done when:** at least three edge cases can be classified consistently by two reviewers.

### 3. Approve Global North/Global South method
- Select a named, public, versioned country classification only if a defensible one is available for the intended use.
- Keep donor/beneficiary role independent from geopolitical grouping.
- Define how contested, mixed, or unclassified cases will appear.
- **Done when:** every country label can be reproduced from a cited methodology, or the field remains explicitly unassigned.

### 4. Approve finance, reach, and currency conventions
- Confirm mechanism and initiative-type controlled vocabularies.
- Define amount concepts and funding stage event model.
- Decide whether the first-release dataset reports original currency only or also a reproducible USD conversion.
- Define reach labels for target, actual, estimated, insured/covered, exposed, and impacted populations.
- **Done when:** a reviewer can distinguish a loan commitment from a disbursement and a beneficiary target from an actual count.

### 5. Choose first-release delivery format
- A static GitHub Pages dashboard with filtered CSV export is implemented as a review prototype; decide whether a spreadsheet/data file or both should also be maintained as the research source of truth.
- Define who may edit, review, publish, and archive data.
- **Done when:** the approved source-of-truth format supports linked/multiple countries, sources, mechanisms, funding events, and organization roles without lossy comma-separated fields.

## P0 — Build evidence base

### 6. Create a candidate initiative registry
- Search official MDB, UN agency, climate/disaster fund, government, regional facility, and credible news sources for 2020 onward.
- Seed candidate searches from SIDS roster, regional risk facilities, national climate/disaster projects, catastrophe risk transfer, contingent financing, resilience infrastructure, and early warning.
- Capture candidates before inclusion decisions; mark each as in scope, needs review, or excluded with reason.
- **Done when:** every candidate has a source URL, discovery note, potential SIDS jurisdiction, likely date, and triage status.

### 7. Verify and normalize initiative records
- Confirm the initiative name, parent/child relationship, country roles, UN region/member status, climate-risk link, record type, and qualifying event.
- Separate initiative from its announcements and individual funding events.
- Deduplicate press releases describing the same project or financing event.
- **Done when:** no in-scope record lacks a documented eligibility rationale or stable ID.

### 8. Code mechanisms and financial events
- Record instrument/facility mechanisms, provider/recipient roles, event stage/date, amount concept, original amount/currency, and funding status.
- Capture project cost separately from finance provided; distinguish commitment, disbursement, ceiling, coverage, and payout.
- Add source notes for disputed, missing, or conflicting values.
- **Done when:** every amount can be interpreted without reading an unstructured note and no unlike concepts are silently aggregated.

### 9. Code organizations, countries, and private-sector participation
- Normalize MDBs, UN bodies, funds, governments, regional organizations, financial companies, insurers, and contractors.
- Record each entity's role and evidence; distinguish finance provider from implementation contractor.
- Link all relevant countries/jurisdictions and their initiative roles.
- Add a North/South category only after the approved method is documented.
- **Done when:** users can filter by organization type and role, country role, SIDS region, and supported grouping.

### 10. Code initiative types, importance, description, and reach
- Apply multi-select types for adaptation, mitigation, capacity building, risk pooling, pre-arranged finance, agriculture, sea wall/coastal protection, transportation, and early warning, plus agreed additional types.
- Write neutral descriptions and importance statements attributed to evidence.
- Capture community counts only with units, geography, timeframe, evidence type, and source.
- **Done when:** target, actual, estimated, covered, exposed, and impacted counts are not conflated; undisclosed reach is explicit.

### 11. Select and verify top links
- Rank up to three relevant sources according to the specification.
- Confirm source title, publisher, date where available, URL availability, and claims supported.
- Ensure primary sources support key finance claims where available.
- **Done when:** every record has at least one credible source and its selected links lead to relevant evidence.

## P0 — Quality assurance and review

### 12. Conduct a pilot double-coding review
- Select a varied pilot set: single-country and regional records, different financing mechanisms, and records with disclosed/missing reach.
- Have a second reviewer independently code inclusion, mechanism, funding stage, amount concept, country/organization roles, and reach type.
- Resolve disagreements by updating definitions and keeping an audit note.
- **Done when:** recurring disagreements are documented and the codebook is revised before bulk entry.

### 13. Validate completeness and avoid double counting
- Check every required field for a value or explicit missingness status.
- Review parent/child records, co-financing, multi-currency values, and overlapping facility/project envelopes.
- Verify all qualifying dates fall in the specified period and are event dates, not just collection dates.
- **Done when:** a reproducible QA checklist has no unresolved critical errors.

### 14. Review sources and claims
- Recheck the top links, financing amounts/stages, population claims, and UN membership references before publication.
- Flag promotional claims as attributed statements; do not present them as independently measured outcomes.
- **Done when:** a reviewer can follow every material claim to evidence or see the limitation.

## P1 — Make it useful to explore

### 15. Build filters, sorting, and exports
- Dashboard prototype implements search, combinable single-value facet filters, per-field sorting, evidence details, filtered CSV, and codebook JSON exports; its controls have been browser-tested against the current candidate record.
- Validate all fields against an agreed multi-record inventory and provide a data codebook with exports. Decide whether multi-select values within individual facets are required for release.
- **Done when:** acceptance criteria in the specification are demonstrated across multiple verified records, including safe amount/reach sorting by comparable units.

### 16. Add transparent summaries
- Dashboard prototype counts filtered records by selectable categories including year, region, organization, type, status, mechanism/amount concepts, and reach disclosures.
- Expand and verify groupings when approved fields and a larger inventory are available. Add financial and reach totals only for compatible concepts, currencies, units, and periods.
- **Done when:** summaries are reproducible from visible records and cannot imply comparability where none exists.

### 17. Add change tracking and maintenance
- Record who reviewed a record and when, along with source changes and corrections.
- Set a periodic recheck schedule for active initiatives and links.
- Keep a dated snapshot of released data.
- **Done when:** users can tell when a record was last verified and what changed since a prior release.

## P2 — Possible extensions

### 18. Add source archive and long-term link resilience
- Store stable identifiers and lawful archived links where available.
- Make archive use consistent with publisher terms and repository policy.

### 19. Add comparative research views
- Explore maps, timelines, mechanism comparisons, and regional breakdowns after the underlying data is validated.
- Avoid presenting visual prominence as evidence of quality or effectiveness.

### 20. Explore outcome and loss data
- Add outcome metrics only when definitions, baselines, observation periods, and attribution limitations are sufficiently documented.
- Keep project outputs and measured disaster-risk reduction distinct.

## Human-review gates before data collection scales

- [ ] Confirm SIDS States plus Associate Members scope.
- [ ] Approve mitigation-only inclusion and post-2020 milestone handling.
- [ ] Approve Global North/South framework or remove the field from the first release.
- [ ] Decide original currency vs USD conversion.
- [ ] Confirm first-release format and who reviews records.
- [ ] Approve the terminology for “impacted individuals/community members” and the distinction from targets, coverage, and exposure.

## Definition of first release

The first release is ready when an agreed pilot inventory has been independently checked, satisfies the P0 acceptance criteria in [SPECIFICATION.md](./SPECIFICATION.md), provides evidence-linked records with explicit unknowns, and supports the agreed review format. It is not ready merely because a large number of candidate initiatives have been entered.
