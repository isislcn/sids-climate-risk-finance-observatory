# SIDS Climate-Disaster Risk Finance Tracker

**Status:** Concept draft for human review  
**Coverage target:** Initiatives announced, approved, committed, or funded from 2020 onward  
**Product type:** Evidence-linked research dataset and sortable project catalogue

## The idea

Build a transparent, searchable tracker of financing and de-risking initiatives that support Small Island Developing States (SIDS) in addressing climate-related disaster risk. For every initiative, the tracker connects the financing mechanism to the places, organizations, activities, timing, scale, and communities it is intended to benefit. Every material claim should lead back to a credible public source.

The tracker is intended to help researchers, practitioners, journalists, and SIDS stakeholders compare what has been announced or financed, how the money is structured, who is involved, and what outcomes are actually documented. It should make evidence gaps visible rather than fill them with estimates presented as facts.

## Why this matters

Climate disasters can cause severe damage in small, exposed economies with limited fiscal capacity. A grant, contingent credit line, insurance payout, catastrophe bond, guarantee, or pooled risk facility can affect when funds become available, who bears risk, and whether a response is financed before or after a disaster. Yet the public record is scattered across development-bank project pages, fund disclosures, government announcements, and news coverage. A structured evidence base can make those arrangements easier to find and compare.

The tracker should distinguish **risk reduction and resilience investment** (for example, early warning or coastal protection) from **financial preparedness and risk transfer** (for example, contingent finance, insurance, and risk pooling). It should also distinguish an announcement from an approval, commitment, disbursement, or actual payout.

## Scope and eligibility

### SIDS membership

Use the UN Office of the High Representative for the Least Developed Countries, Landlocked Developing Countries and Small Island Developing States (UN-OHRLLS) SIDS definition and membership as the authority for inclusion. The UN describes SIDS as a distinct group of **39 States and 18 Associate Members of UN regional commissions** in three regions: Caribbean, Pacific, and Atlantic, Indian Ocean and South China Sea (AIS).

For the initial inventory, include initiatives with a named SIDS State or Associate Member as a beneficiary, participant, or covered jurisdiction. Keep associate members eligible, but identify their membership status so users can filter them separately. Store the applicable roster source and the date checked; membership and regional assignment must not be inferred solely from geography.

### Initiative inclusion

Include a publicly documented initiative when all of the following apply:

1. At least one UN-listed SIDS State or Associate Member is a named beneficiary, participant, or covered jurisdiction.
2. The initiative has a clear climate-change adaptation, mitigation, climate-disaster preparedness/response, resilience, or climate-risk financing connection.
3. A financing or de-risking mechanism is documented, or the initiative demonstrably builds capacity for such a mechanism.
4. At least one credible public source supports the initiative's existence and basic description.
5. Its announcement, approval, financial commitment, funding, or implementation milestone falls on or after **1 January 2020**. Record the exact event and date that qualifies it.

Include both country-level and multi-country/regional initiatives. Include proposed or announced initiatives only when their status is labeled accurately. Do not treat a proposal, total project cost, maximum facility size, commitment, disbursement, and payout as interchangeable.

### Exclusions and boundaries

- Exclude general development projects with no evidenced connection to climate risk or climate action.
- Exclude purely domestic initiatives with no publicly documented financing/de-risking or relevant capacity-building component.
- Do not count an umbrella facility and its subprojects as separate investments without explicit parent/child relationships and safeguards against double counting.
- Do not infer participating countries, private-sector involvement, funding received, affected population, or project impact from a source that does not support the claim.
- Do not equate a source's description of a country as “developing” with a Global North/Global South classification.

## Intended users and jobs to be done

- **Researchers and students:** find comparable initiatives by year, country, region, mechanism, sector, financier, or scale; trace claims to sources.
- **SIDS governments and regional organizations:** identify relevant financing designs and regional facilities, and see what is disclosed or missing.
- **Funders and development practitioners:** distinguish risk reduction from risk transfer and compare funding stages and partners.
- **Journalists and civil society:** verify who announced, financed, implemented, or benefited from an initiative and what evidence supports stated reach.

## Core experience

The minimum useful product is a well-documented dataset that can be summarized and sorted by every requested parameter. A web interface or spreadsheet should provide:

- Search by initiative name, country/jurisdiction, organization, and source text.
- Filters for year, SIDS region, membership status, finance mechanism, initiative type, participating-country grouping, organization type, funding status/stage, and disclosed investment amount.
- Sortable columns for all normalized fields, with explicit “not disclosed” values rather than blanks that could be mistaken for zero.
- Initiative detail views with a concise summary, project description, importance/rationale, country and organization roles, financial amounts and stages, community-reach evidence, and up to three ranked relevant source links.
- Clear source-to-claim traceability, last-checked dates, and uncertainty notes.
- Aggregate summaries that disclose their coverage, date range, filters, and treatment of missing values and overlapping amounts.

## Evidence and editorial principles

Prioritize multilateral development banks, UN agencies, climate and disaster-risk funds, government and regional facility publications, and primary project documents. Reputable news coverage may corroborate or contextualize but should not replace an available primary source for financial or membership claims.

Use at least one source that verifies the initiative and its SIDS connection. Add sources for financial amounts, dates/stages, partner roles, and beneficiary reach when those claims are made. Record a citation for each material field where practicable; the three “top links” are a compact reading list, not a substitute for field-level evidence.

Keep these distinctions visible:

- announced / proposed / approved / committed / contracted / disbursed / paid out / completed;
- financing amount vs project cost vs co-financing vs leveraged finance vs insurance coverage vs payout;
- actual beneficiary count vs target vs estimate vs population exposed;
- financial institution / funder vs executing or implementing entity vs insurer, broker, investor, or private-sector contractor;
- country where risk occurs vs donor/contributor country vs other participating country.

When a value is unavailable, use “Not disclosed” (or the appropriate controlled value), not zero. Report uncertainty and conflicting sources. Preserve original currency and amount alongside any normalized USD conversion and document the conversion date and method.

## Intended outcome and non-goals

**Outcome:** a dependable, legible evidence base for comparing publicly documented SIDS climate-disaster risk-financing initiatives since 2020.

**Not in the first release:** an exhaustive audit of every climate-finance flow; a measure of project effectiveness; a substitute for official financial reporting; a live transactional database; predictions of disaster losses; independent verification of every beneficiary claim; or a normative judgment that an instrument is beneficial simply because it is labeled “resilient” or “green.”

## Success measures

- Every included record satisfies the inclusion rules and identifies its qualifying date.
- Every record has a traceable credible source, a named SIDS beneficiary/participant, a status, and a financing mechanism or a documented capacity-building link to one.
- Users can filter and sort on all required dimensions without conflating missing, zero, and unreported data.
- Financial figures retain amount, currency, financial concept, stage, and source; duplicate/overlapping totals are not silently added.
- Community reach is presented with its evidence type and time horizon, or explicitly marked not disclosed.
- A reviewer can reproduce key summary totals from the underlying records and stated filters.

## Questions for human review

1. Should the first release cover only SIDS States, or both States and UN regional-commission Associate Members? This draft includes both and labels membership status.
2. Should mitigation-only initiatives qualify when climate-disaster risk reduction is not explicit? This draft includes mitigation when the climate connection is documented, and tags disaster-risk relevance separately.
3. Which Global North/Global South framework should the project adopt? There is no single uncontested UN membership classification. This draft requires a named, versioned classification source and retains the raw country role; it does not assign categories by inference.
4. Should investment amounts be normalized to USD, and if so, which exchange-rate source and date convention should be used? This draft retains reported currencies and requires any conversion to be reproducible.
5. Is the deliverable initially a spreadsheet, static web catalogue, or both? The data requirements are format-neutral; a spreadsheet is a practical review-stage starting point.

## Reference starting points

- [UN-OHRLLS: About Small Island Developing States](https://www.un.org/ohrlls/content/about-small-island-developing-states) — definition and regions.
- [UN-OHRLLS: List of SIDS](https://www.un.org/ohrlls/content/list-sids) — membership roster.
- Source quality and initiative records should be validated against the cited institution's current publication at research time; the references above define scope, not a project inventory.
