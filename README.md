# data-platform

[![dbt CI](https://github.com/youbaAgn/data-platform/actions/workflows/dbt-ci.yml/badge.svg)](https://github.com/youbaAgn/data-platform/actions/workflows/dbt-ci.yml)

Data platform built with dbt-core, DuckDB and GitHub Actions.

## Stack
- **dbt-core** — data transformations
- **DuckDB** — local analytical database
- **GitHub Actions** — CI/CD

## Project Structure
data-platform/
└── jaffle_shop/    # dbt project


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
dbt run
dbt test

