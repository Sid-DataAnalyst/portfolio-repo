# Local project review — 11 October 2026

This records the initial scan and preparation. The subsequent organization and HR source-version change are recorded in [REPOSITORY-ORGANIZATION.md](./REPOSITORY-ORGANIZATION.md).

## Scope and evidence

- Scanned accessible G: folders for PBIX, PBIT, PBIP, TWB, TWBX, and Hyper files, excluding protected system and installed application folders and the new repository clone.
- Found 167 Power BI files and 107 Tableau files. Counts include practice files, course examples, old versions, and duplicates; they are not counts of original completed projects.
- Found two groups of byte-identical files, representing three extra copies. Originals were preserved.
- Selected nine candidates from Portfolio Projects, as requested by the owner. No client-demo or training folders were imported.
- Copied 151 files, verifying every copy against its source SHA-256 hash. PBIP report/model folders were copied together; local .pbi caches were excluded.
- Parsed 67 copied JSON files without errors and inspected all five Tableau packaged workbook XML definitions.

Local audit files are outside the Git repository in `G:\Portfolio Projects\portfolio-preparation`: `project-inventory.csv`, `duplicate-files.csv`, and `copy-manifest.csv`. The manifest records every source, destination, hash, and size.

## Findings that need attention

All four Power BI semantic models contain external file or SQL source expressions. Original source definitions were preserved. They require source configuration and refresh testing on the machine used for the portfolio. No new source datasets have been bundled with the PBIP candidates.

Each selected Tableau package has one embedded data entry. The embedded data contents have not been reviewed. The Accounts Payable workbook has a dashboard named `Kasmo - DB`; confirm ownership, permission to share, and whether this branding should be replaced. A file being in Portfolio Projects does not establish its publication rights.

The candidates have not been opened in Power BI Desktop or Tableau Desktop during this preparation. Packaging checks do not establish that visuals render, calculations are correct, data refresh works, or data is suitable for public sharing.

## Recommended completion order

1. Consumer Sales and Tableau Sales YTD / MTD: review a related sales story in both tools and confirm dataset provenance.
2. Power BI HR Data Quality and Tableau HR Attrition: confirm synthetic/public employee data, document cleaning rules and attrition definitions.
3. Finance and Manufacturing: verify source permission, KPI formulas, and workbook interactions.
4. Daily Sales and Retail Orders: assess overlap with existing sales projects and retain those that demonstrate distinct skills.
5. Accounts Payable: resolve branding and embedded data review before featuring it publicly.

For each selected project, add a business question, data provenance, preparation/model explanation, key calculations, screenshots, and findings supported by the workbook. Use public or synthetic replacement data when required. Credit any templates or tutorials.

## GitHub state

The public repository was cloned successfully. Git Credential Manager returned no saved GitHub account. Write access was not tested. All changes remain local; no files were staged, committed, or pushed during preparation.
