# Review and publish the portfolio

The prepared local repository is `G:\Portfolio Projects\portfolio-repo`. Its origin is `https://github.com/Sid-DataAnalyst/portfolio-repo.git`.

## Review first

Complete PROJECT-REVIEW.md, open selected workbooks in Power BI Desktop or Tableau Desktop, fix sources, test refresh and interactions, and add screenshots and supported findings. Remove or postpone candidates you do not want to publish, and update the root index accordingly.

All nine Power BI projects are under `power-bi`; all five Tableau projects are under `tableau`. The existing five project folders were moved locally with contents preserved. See REPOSITORY-ORGANIZATION.md for source versions and backups.

## Upload using GitHub Desktop

1. Sign into your GitHub account in GitHub Desktop.
2. Choose File > Add local repository and select `G:\Portfolio Projects\portfolio-repo`.
3. Review changed files. Select only completed, approved projects and documentation. Ensure README links match the projects selected.
4. Create a branch such as `portfolio-expansion`, commit selected changes, and publish the branch.
5. Open a pull request and review the final file set before merging into main.

Do not share your password or access token in chat. The supplied email address alone does not authenticate Git access.

## Optional Git commands

After review, run these in PowerShell. Add only completed project paths.

```powershell
Set-Location -LiteralPath 'G:\Portfolio Projects\portfolio-repo'
git switch -c portfolio-expansion
git status --short
# Stage the five existing folders' old paths and their new locations as one change.
git add -A -- '01-it-helpdesk-performance-tracker' '02-global-travel-carbon-footprint-dashboard' '03-sales-analysis-overview' '04-hr analytics overview' '05-claim management' 'power-bi/01-it-helpdesk-performance-tracker' 'power-bi/02-global-travel-carbon-footprint-dashboard' 'power-bi/03-sales-analysis-overview' 'power-bi/04-hr-analytics-overview' 'power-bi/05-claim-management'
# Add only additional candidates whose review is complete. Example:
git add -- 'power-bi/consumer-sales'
# Update indexes to match projects being published, then stage documentation.
git add -- README.md .gitignore .gitattributes docs 'power-bi/README.md' 'tableau/README.md'
git diff --cached --stat
git diff --cached --check
git commit -m "Add reviewed BI portfolio projects"
git push -u origin portfolio-expansion
```

Complete any browser authentication yourself, then open a pull request on GitHub. This preparation has not performed a commit or push.
