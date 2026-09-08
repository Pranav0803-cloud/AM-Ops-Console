# AM Ops Console

A live operations dashboard for Even Healthcare's Account Management team — tracks policies, corporate clients, and AM-level performance in one place.

**Live URL:** https://pranav0803-cloud.github.io/AM-Ops-Console/

## What it does

The dashboard pulls live data from the team's Google Sheet ("Master Sheet" tab) via a deployed Google Apps Script web app, and renders it across five views:

- **Master Data** — raw row-level policy/client data
- **Corp-Wise View** — corporate clients grouped by organization, click a row to expand and see that org's policies
- **Policy-Level View** — organizations grouped the same way, click a row to expand and see every policy for that org, both active and past/expired
- **AM Workbench** — account manager-level rollups
- **Executive Dashboard** — headline KPIs (active ARR, realised revenue, client counts, etc.)

All business logic (active vs. expired, in-scope filtering, revenue estimates, corp/org rollups) lives in the dashboard's own JavaScript. The Apps Script backend is a simple read-only JSON/JSONP feed — it does no processing of its own.

## How it's hosted

This is a static site. GitHub Pages serves `index.html` directly from the `main` branch root — there's no build step.

## Making updates

The dashboard is a single self-contained HTML file (`index.html`) with inline CSS and JS. To update it:

1. Edit `index.html` (or get an updated version of it).
2. Go to this repo's **Add file → Upload files** (or `github.com/Pranav0803-cloud/AM-Ops-Console/upload/main`).
3. Upload the new `index.html`, overwriting the existing one.
4. Commit directly to `main`.
5. GitHub Pages rebuilds automatically (usually within a minute or two) — check the **Actions** tab for the "pages build and deployment" run, then hard-refresh the live URL.

## Data source

Live data comes from a Google Apps Script deployed against the team's Google Sheet. The Apps Script URL is set in `index.html` as the `APPS_SCRIPT_URL` constant near the top of the script. If the badge on the live site shows "Sample data — Master Sheet not connected," check that this URL is still valid and that the Apps Script deployment hasn't been revoked or redeployed under a new URL.
