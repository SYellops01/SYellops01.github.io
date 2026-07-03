---
title: "Warehouse Pipeline Speed-Up"
subtitle: "Cutting nightly transformation runtime from 3 hours to 25 minutes"
slug: pipeline-optimization
model_name: "stg_orders_incremental"
summary: "Rebuilt a full-refresh pipeline as incremental models, cutting nightly runtime by 85%."
order: 2
thumbnail: thumbs/lineage-b.html
stack: ["dbt", "Snowflake", "Airflow", "Python"]
demo_url: ""
code_url: ""
---

## The problem

The nightly pipeline rebuilt every table from scratch, which took just
under three hours. As data volume grew, it started missing the window
before the first analysts logged on, and any single failure meant a
morning of stale dashboards.

## What I built

- Rewrote the largest, slowest-growing models as **incremental dbt
  models**, so only new or changed rows were processed each run.
- Added **source freshness checks** and Airflow alerting so failures
  surfaced immediately instead of being discovered by an analyst.
- Introduced **clustering keys** on the largest warehouse tables to cut
  scan time on downstream queries.

## Impact

- Nightly runtime dropped from ~3 hours to ~25 minutes.
- Warehouse compute cost for the pipeline fell by roughly a third.
- Dashboards are now reliably fresh before the workday starts.

## Notes

Same as the first project — swap this content for your own. Keep the
front matter fields (`title`, `summary`, `stack`, `order`, `thumbnail`)
since the homepage and layout both read from them.
