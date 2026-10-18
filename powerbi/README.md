# Power BI Dashboard Setup Guide

**Project:** Sales Performance & Business Analytics  
**Dataset:** `data/sales_data.csv` (synthetic practice data)  
**Author:** Palak Gandhi

## 1. Import the data
1. Open Power BI Desktop.
2. Select **Home → Get data → Text/CSV**.
3. Choose `data/sales_data.csv`.
4. Select **Transform Data** to inspect data types.
5. Set `Order_Date` to Date; set `Quantity` to Whole Number; set `Unit_Price`, `Sales`, `Cost`, and `Profit` to Decimal Number or Fixed Decimal Number.
6. Select **Close & Apply**.

## 2. Create a Date table
From **Modeling → New table**, add:

```DAX
Date =
ADDCOLUMNS(
    CALENDAR(MIN(sales[Order_Date]), MAX(sales[Order_Date])),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month", FORMAT([Date], "MMM"),
    "Year-Month", FORMAT([Date], "YYYY-MM")
)
```

Then select the Date table and choose **Table tools → Mark as date table**, selecting `Date[Date]`. Create a relationship from `Date[Date]` to `sales[Order_Date]`. Sort `Date[Month]` by `Date[Month Number]` when using month names across a single year; use `Year-Month` for a multi-year timeline.

## 3. Add DAX measures
Open `dax_measures.txt` and create each measure using **Modeling → New measure**. Add the Date table before adding the optional year-over-year measures.

## 4. Suggested report layout
- **KPI cards:** Total Sales, Total Profit, Total Orders, Total Customers, Average Order Value.
- **Line chart:** `Date[Year-Month]` with Total Sales and Total Profit.
- **Bar chart:** Category by Total Sales.
- **Bar chart:** Region by Total Sales.
- **Bar chart:** Top 10 Product_Name by Total Sales (use a Top N visual filter).
- **Table or bar chart:** State by Total Sales and Total Profit.
- **Donut chart:** Customer_Segment by Total Sales.
- **Slicers:** Date, Region, Category, Customer_Segment.

## 5. Quality checks
- Confirm that sales, profit, and order totals match calculations from the imported dataset.
- Check whether negative profits exist and investigate them rather than hiding them.
- Use actual chart outputs and measured values in your README.
- The earlier dashboard images are visual mockups only; their displayed figures are not verified results from this dataset.

## 6. Publish to GitHub
Save your Power BI report as `sales_performance_dashboard.pbix` on your own device. GitHub may not preview PBIX files in the browser, so also export a screenshot or PDF and place the preview image in `images/`.
