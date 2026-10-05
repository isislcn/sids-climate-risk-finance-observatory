# SIDS Climate-Disaster Risk Finance Dashboard

Static, responsive GitHub Pages prototype for exploring evidence-linked climate-disaster risk finance and de-risking initiatives involving UN-listed Small Island Developing States (SIDS).

## Preview

Open `site/index.html` in a browser. No build step, package manager, external JavaScript library, or API key is required. The pilot data is embedded in the page so it also works from a local `file://` URL.

## Publish on GitHub Pages

1. Push this project folder's contents to the root of a GitHub repository.
2. In **Settings → Pages → Build and deployment**, select **GitHub Actions** as the source.
3. The workflow at `.github/workflows/deploy-pages.yml` deploys the `site/` folder on pushes to `main` or `master`, or via manual workflow dispatch.

The site uses relative document links and includes no root-relative asset paths, so it works as a GitHub Pages project site.

## Dashboard features

- Search initiatives; filter by year, region tag, financing mechanism, initiative type, funding status, country disclosure and grouping, membership/review status, organization and role, source publisher, reach disclosure, and amount disclosure.
- Sort by the available research fields (including organizations and roles, amount concept, timing, importance, reach, and project description), or use sortable table columns.
- Choose a summary dimension to count filtered records by year, region, organization, initiative type, status, financing concept, amount disclosure, reach, and other listed fields.
- Open a record detail view with organizations/roles, SIDS eligibility caveat, financing timing, importance, reach, and up to three sources.
- Export the current filtered view to CSV and field definitions/conventions to a separate codebook JSON.
- Summary cards and selectable dimension breakdowns recalculate with the filters.
- Responsive layout, keyboard-accessible controls, and reduced-motion support.

## Data and limitations

The current catalogue contains one **research candidate**, not an eligible or exhaustive SIDS initiative inventory. It describes CCRIF's 2024 report of funding through CDB and the Canada-CARICOM Climate Adaptation Fund supporting seven member countries to increase coverage and make national social-protection systems more shock responsive. The source page does not identify the seven countries, so inclusion of any UN-listed SIDS beneficiary is unverified; the candidate must not be counted as confirmed SIDS finance until that is checked. It also does not report an amount or individual beneficiary count. Do not interpret the candidate as a regional total or verified project impact.

Amount sorting is grouped by currency and financing concept, and reach sorting by unit and evidence type, to avoid ranking unlike measurements as though they were comparable. Summary views count records in categories; they do not imply funding or beneficiary totals.

The UN-OHRLLS [SIDS list](https://www.un.org/ohrlls/content/list-sids) and [SIDS overview](https://www.un.org/ohrlls/content/about-small-island-developing-states) define the membership and regions. The dashboard's research criteria, field definitions, and inclusion rules are in [SPECIFICATION.md](./SPECIFICATION.md); product framing is in [CONCEPT-IDEA.md](./CONCEPT-IDEA.md); planned research and review tasks are in [BACKLPG.md](./BACKLPG.md).

Before adding records, retain the schema and evidence distinctions in the specification. In particular, do not mix commitments, disbursements, project costs, coverage, guarantees, or payouts; do not treat targets or coverage as actual individual beneficiaries; and do not infer Global North/Global South categories without a cited, versioned method.
