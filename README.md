# data-platform

[![dbt CI](https://github.com/youbaAgn/data-platform/actions/workflows/dbt-ci.yml/badge.svg)](https://github.com/youbaAgn/data-platform/actions/workflows/dbt-ci.yml)

Data platform built with dbt-core, DuckDB and GitHub Actions.

## Stack
- **dbt-core** — data transformations
- **DuckDB** — local analytical database
- **GitHub Actions** — CI/CD

## Project Structure
```
data-platform/
└── jaffle_shop/
    ├── seeds/              # raw CSV data (customers, orders, payments)
    ├── models/
    │   ├── staging/        # cleaning layer (views)
    │   └── marts/          # business layer (tables)
    ├── .github/
    │   └── workflows/
    │       └── dbt-ci.yml  # CI/CD pipeline
    └── dbt_project.yml
```

## Architecture

```
seeds (CSV)
    ↓
staging (views)   — rename, cast, clean
    ↓
marts (tables)    — joins, aggregations, business logic
```

## Getting Started

### Prerequisites
- Python 3.12+
- Git

### Run locally
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install dbt-core dbt-duckdb
cd jaffle_shop
dbt seed
dbt run
dbt test
```

### Generate documentation
```bash
cd jaffle_shop
dbt docs generate
dbt docs serve
```
Opens at http://localhost:8080

## Models

| Model | Layer | Type | Description |
|-------|-------|------|-------------|
| `stg_customers` | staging | view | Cleaned customers |
| `stg_orders` | staging | view | Cleaned orders |
| `stg_payments` | staging | view | Cleaned payments |
| `dim_customers` | marts | table | One row per customer with order stats |
| `fct_orders` | marts | table | One row per order with payment amount |

## Tests

13 data tests covering `unique`, `not_null` and `accepted_values` on all models.
