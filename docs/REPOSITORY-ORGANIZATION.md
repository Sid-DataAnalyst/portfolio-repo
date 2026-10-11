# Repository organization — 11 October 2026

The unified portfolio uses this structure:

```text
portfolio-repo/
  README.md
  power-bi/
    README.md
    01-it-helpdesk-performance-tracker/
    02-global-travel-carbon-footprint-dashboard/
    03-sales-analysis-overview/
    04-hr-analytics-overview/
    05-claim-management/
    consumer-sales/
    daily-sales/
    hr-data-quality/
    retail-orders/
  tableau/
    README.md
    accounts-payable/
    finance-dashboard/
    hr-attrition/
    manufacturing/
    sales-ytd-mtd/
  docs/
```

## Sources and versions

The five existing Power BI projects came from [portfolio-repo](https://github.com/Sid-DataAnalyst/portfolio-repo). All 18 existing project files were moved into power-bi and verified against their original SHA-256 hashes. HR and claims folder names were normalized to remove spaces. Root links were updated.

[PowerBI_2026](https://github.com/Sid-DataAnalyst/PowerBI_2026) could not be fetched anonymously. A local Git checkout exists at `G:\Portfolio Projects\PowerBI_2026`, points to that remote, and has HEAD `6a23524` (Revert "Deleted by mistake"). Its tracked working files were clean when inspected. Its current remote contents remain unverified.

The HR Data Quality project now contains the 33 project files from that checkout, excluding local .pbi settings. Four report-definition files differed from the earlier Portfolio Projects candidate. The earlier complete workbook folder was preserved at `G:\Portfolio Projects\portfolio-preparation\hr-data-quality-local-variant`. Neither original source folder nor the PowerBI_2026 repository was modified.

The other additional Power BI candidates and all five Tableau candidates came from the local Portfolio Projects folders. They remain subject to the owner's review before publication.

## Audit and publication

The local preparation folder contains `reorganization-manifest.csv` for the moves and `hr-repository-copy-manifest.csv` for the HR import. The earlier copy manifest records the first preparation step; its old root destinations and HR source version have been superseded by these newer manifests.

The repository organization is a local draft. Nothing has been staged, committed, or pushed. Only files in portfolio-repo should be submitted for publication; the backup, manifests, and nested Git checkout stay outside it.

Git will recognize moved files as renames when staged. The publishing guide uses explicit old and new paths to record both removals and additions.
