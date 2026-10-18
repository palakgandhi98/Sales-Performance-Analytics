# SQL Analysis — Sales Performance & Business Analytics

This folder contains MySQL scripts for analyzing the sample sales dataset.

## Files
- `01_create_sales_table.sql` — creates the `sales` table.
- `02_sales_analysis_queries.sql` — KPI, monthly trend, regional, category, product, customer segment, state, weekday, AOV, and month-over-month growth queries.

## How to run
1. Create a MySQL database for this project.
2. Run `01_create_sales_table.sql`.
3. Import `data/sales_data.csv` into the `sales` table, matching the column names and date format (`YYYY-MM-DD`).
4. Run `02_sales_analysis_queries.sql` query by query.
5. Record actual results in the main README; do not use unverified sample dashboard numbers.

## Notes
- The queries assume MySQL 8.0+ for common table expressions and window functions.
- `average_row_sales` in the KPI query is average sales per dataset row, not necessarily average order value. The separate AOV query calculates average order value using order-level totals.
- This is a portfolio practice project using synthetic data.
