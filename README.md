# FMCG Promotion Effectiveness & Customer Growth Analytics

> A portfolio project in progress: extending a retail revenue-growth baseline into a reproducible SQL/Python workflow for customer segmentation, causal promotion evaluation and budget decisions.

![Status](https://img.shields.io/badge/status-work%20in%20progress-orange)
![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![DuckDB](https://img.shields.io/badge/DuckDB-planned-FFF000?logo=duckdb&logoColor=black)
![Power BI](https://img.shields.io/badge/Power%20BI-planned-F2C811?logo=powerbi&logoColor=black)
![License](https://img.shields.io/badge/code-MIT-green)

## Project Positioning

This repository is an independently developed portfolio extension of the MIT-licensed project [`medhanshrajdeo/revenue-growth-analytics`](https://github.com/medhanshrajdeo/revenue-growth-analytics).

The imported baseline provides a Python workflow for beverage filtering, descriptive promotion lift, rule-based household segmentation, commercial KPIs and directional what-if scenarios. My extension focuses on the analytical gaps that matter in a Data Analyst, Business Analyst or Consumer Insights interview:

- a reproducible DuckDB and SQL analytical layer;
- a household-level Customer 360 table;
- RFM, cohort retention and validated K-Means segmentation;
- matched Difference-in-Differences and event-study diagnostics;
- robustness, placebo and sensitivity checks;
- a redesigned four-page Power BI decision dashboard.

See [PROJECT_PLAN.md](PROJECT_PLAN.md) for the delivery plan and [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for attribution.

## Current Status

| Workstream | Status | Evidence |
|---|---|---|
| Import source baseline and preserve history | Complete | `upstream/main` retained |
| Attribution and project scope | Complete | Project plan and third-party notice |
| Obtain raw dunnhumby data | Pending | Raw files are intentionally not distributed |
| Reproduce and validate baseline results | Pending | No independent reproduction claim yet |
| DuckDB/SQL data model | Planned | Schema and quality checks to be added |
| Customer 360, RFM and cohort analysis | Planned | Independent extension |
| K-Means segmentation and stability checks | Planned | Independent extension |
| Matching, DiD and event study | Planned | Independent extension |
| Power BI decision dashboard | Planned | Four-page redesign |

## Business Question

How should an FMCG manufacturer or grocery retailer allocate a limited promotion budget across products, stores and customer segments?

The analysis is designed to separate three different questions:

1. **Description:** What happened during promoted and non-promoted periods?
2. **Incrementality:** How much of the change is plausibly attributable to the promotion?
3. **Decision:** Which promotions should be expanded, redesigned or stopped under explicit budget and margin assumptions?

## Dataset

The project uses the dunnhumby **Complete Journey** dataset, which represents approximately two years of household-level grocery activity for 2,500 frequent-shopper households. It includes transactions, product hierarchy, stores, campaigns, coupons, redemptions, display/mailer indicators and partial household demographics.

Official source: [dunnhumby Source Files](https://www.dunnhumby.com/source-files/)

Raw data are not committed to this repository. Download the dataset from the official source and place the expected CSV files in `data/raw/`.

## Analytical Roadmap

### 1. Reproducible Data Foundation

- document table grain, primary keys and joins;
- create DuckDB staging and analytical tables;
- test row counts, uniqueness, missingness and invalid values;
- build product-store-week and household-level datasets;
- record every reproduction difference from the imported baseline.

### 2. Customer 360 and Segmentation

- calculate Recency, Frequency and Monetary features;
- measure basket value, active weeks, purchase intervals and category breadth;
- build customer and revenue cohort-retention matrices;
- compare rule-based RFM segments with K-Means clusters;
- test cluster stability across seeds and time windows.

### 3. Promotion Effectiveness

The imported baseline compares promoted and non-promoted unit velocity. That measure is descriptive and may be affected by seasonality, product selection, store differences and pre-existing trends.

The planned extension will:

- construct a complete `product_id × store_id × week_no` panel;
- define promotion episodes using display, mailer and discount signals;
- match treated observations to comparable non-promoted controls;
- report covariate balance and common support;
- estimate Difference-in-Differences models;
- visualise event-time coefficients and test pre-trends;
- run alternative-window, placebo and outlier sensitivity checks.

### 4. Commercial Decision Layer

- translate model estimates into incremental units and revenue ranges;
- compare category, SKU, store and customer-segment heterogeneity;
- distinguish observed facts, estimated effects and business assumptions;
- model budget scenarios under explicit gross-margin and execution-cost assumptions.

## Causal and Commercial Boundaries

- Descriptive promotion lift is not presented as a causal estimate.
- A causal interpretation requires credible treatment-control comparability, parallel trends and robustness evidence.
- Coupon redemption is a post-treatment customer choice and will not be used naively as the treatment definition.
- Complete product cost and promotion execution cost are unavailable; profit and ROI will therefore be shown only as sensitivity scenarios.
- Demographic profiling is limited because demographics are available for only part of the household panel.

## Imported Baseline

The source project currently contains:

- Python cleaning and transformation modules in `src/`;
- narrative notebooks in `notebooks/`;
- aggregated Power BI exports in `data/powerbi_exports/`;
- charts and presentation assets in `outputs/`;
- a presentation-visual generator in `scripts/`.

The baseline repository reports results such as beverage revenue, promotion share, product lift and household segment summaries. These are inherited reference outputs and are **not yet presented as independently reproduced results in this portfolio**.

## Repository Structure

```text
fmcg-promotion-causal-analytics/
├── data/
│   ├── raw/                        # Local only; not committed
│   ├── processed/                  # Regenerable intermediates
│   └── powerbi_exports/            # Reviewable baseline aggregates
├── notebooks/                      # Baseline notebooks; extensions planned
├── outputs/                        # Charts and presentation assets
├── scripts/                        # Supporting scripts
├── src/                            # Baseline Python modules
├── PROJECT_PLAN.md                 # Portfolio delivery plan
├── THIRD_PARTY_NOTICES.md          # Attribution and data notice
├── requirements.txt
└── README.md
```

Planned additions include `sql/`, `tests/`, `reports/` and `powerbi/` directories.

## Running the Imported Baseline

The commands below describe the imported baseline and have not yet been recorded as a successful independent end-to-end reproduction in this repository.

```powershell
pip install -r requirements.txt

python -m src.data_cleaning
python -m src.beverage_filtering
python -m src.promotion_metrics
python -m src.segmentation
python -m src.kpi_builder
```

Before running, download the Complete Journey CSV files and place them in `data/raw/` as described by the source project.

## Portfolio Evidence Standard

A feature will be described as complete only when the repository contains:

- runnable code or SQL;
- input and output definitions;
- validation checks;
- an interpretable chart or table;
- a written limitation;
- a Git commit showing the work.

## Attribution and License

Selected source code remains subject to the original MIT License and copyright notice. The raw dunnhumby data are governed separately by the data provider's terms and are not redistributed here.

For full details, see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Portfolio Author

**Lotus-Yuhan**

Target roles: Data Analyst, Business Analyst and Consumer Insights Analyst.
