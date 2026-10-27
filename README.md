# Sales & Business Performance Dashboard

**An interactive retail analytics dashboard built with Microsoft Power BI**

![Sales & Business Performance Dashboard](screenshots/dashboard_preview.png)

## Project Overview

This project uses Power BI to analyze sales performance for a **fictional retail business** across 2024 and 2025. It converts transactional data into an interactive management dashboard that tracks revenue, profitability, order volume, product performance, and regional sales. The dataset is synthetic and does not represent a real company.

## Business Problem

Retail managers need a clear view of sales and profitability across regions and product categories. Transaction-level records are difficult to interpret quickly, making it harder to identify strong products, compare markets, and monitor performance over time.

**Business question:** How can management use sales data to understand overall performance and identify opportunities to improve revenue and profitability?

## Objectives

- Monitor total sales, total profit, unique orders, and profit margin.
- Compare sales across product categories and geographic regions.
- Identify the ten products generating the most revenue.
- Examine sales trends over time.
- Enable interactive analysis by region, category, and order date.

## Dashboard Preview

![Dashboard screenshot](screenshots/dashboard_preview.png)

The report includes four KPI cards, a sales trend chart, category and regional comparisons, a top-products ranking, and interactive slicers for **Region**, **Category**, and **OrderDate**.

## Key Performance Indicators

*Values below are taken from the dashboard screenshot, with no slicers applied.*

| KPI | Dashboard result | Meaning |
| --- | ---: | --- |
| Total Sales | Rs. 169.72M | Total revenue generated |
| Total Profit | Rs. 24.09M | Total profit recorded |
| Total Orders | 1,200 | Distinct order IDs (shown as 1.200K on the current card) |
| Profit Margin | 14.20% | Profit as a percentage of sales |

Figures are rounded for display.

## Data and Tools

- **Dataset:** Synthetic retail transactions dated 2024–2025, with 1,200 order records.
- **Fields:** OrderID, OrderDate, Region, District, City, CustomerSegment, Category, SubCategory, ProductName, Quantity, UnitPrice, Discount, Sales, and Profit.
- **Tools:** Microsoft Power BI Desktop, Power Query, DAX, Git, and GitHub.

### Data Preparation

Power Query was used to review data types, ensure dates and numeric fields were interpreted correctly, and check important fields for errors or missing values. The cleaned data was loaded into the Power BI model for reporting.

## DAX Measures

The measures below assume the imported table is named `sales_data`.

**Total Sales** — total sales amount in the current filter context.

```dax
Total Sales = SUM('sales_data'[Sales])
```

**Total Profit** — total profit in the current filter context.

```dax
Total Profit = SUM('sales_data'[Profit])
```

**Total Orders** — number of unique order IDs.

```dax
Total Orders = DISTINCTCOUNT('sales_data'[OrderID])
```

**Profit Margin** — profit divided by sales, with a safe fallback when sales are zero.

```dax
Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)
```

Format **Profit Margin** as a percentage in Power BI.

## Dashboard Visualizations

| Visual | Business purpose |
| --- | --- |
| KPI cards | Summarize overall sales, profit, orders, and profit margin |
| Sales trend line chart | Explore changes in sales over time |
| Sales by Category | Compare Technology, Furniture, and Office Supplies |
| Sales by Region | Compare Western, Central, Southern, Northern, and Eastern regions |
| Top 10 Products by Sales | Identify leading products by revenue |
| Region, Category, and Date slicers | Filter the entire report interactively |

## Key Findings

The following observations are based on the **unfiltered dashboard screenshot**:

1. **Sales and profitability:** The business generated approximately **Rs. 169.72 million** in sales and **Rs. 24.09 million** in profit, equivalent to a **14.20%** overall profit margin.
2. **Leading category:** **Technology** generates the largest sales revenue, substantially ahead of Furniture and Office Supplies.
3. **Leading region:** The **Western** region contributes the highest sales revenue among the five regions shown.
4. **Leading product:** **Laptop Pro** ranks first by sales revenue in the Top 10 Products chart.
5. **Geographic differences:** Northern and Eastern regions contribute less sales revenue than Western, Central, and Southern regions in the current view.

**Interpretation note:** Revenue leadership does not necessarily mean highest profitability. Further analysis of profit by product, category, and region would be required before making investment decisions. The current screenshot's trend line shows fine-grained date fluctuations; a monthly aggregation would make month-to-month conclusions more reliable.

## Recommendations and Next Steps

- Compare **profit**, not only sales, by region and category to identify profitable growth opportunities.
- Investigate what drives strong sales in the Western region and whether those approaches can be adapted elsewhere.
- Review margins for top-selling products to assess whether high revenue translates into strong profitability.
- Add a Year-Month field and show one point per month to support clearer trend analysis.
- Consider additional measures such as average order value, year-over-year sales growth, and discount impact.

These are suggested analyses, not confirmed causal findings.

## Repository Structure

```text
sales-business-performance-dashboard/
├── data/
│   └── sales_data.csv
├── dashboard/
│   └── sales_dashboard.pbix
├── screenshots/
│   └── dashboard_preview.png
└── README.md
```

## How to Use

1. Download or clone the repository.
2. Open `dashboard/sales_dashboard.pbix` in **Power BI Desktop**.
3. If prompted about the data source, update the CSV file path to `data/sales_data.csv` on your computer and refresh.
4. Use the Region, Category, and OrderDate slicers to explore the results.

> **Note:** GitHub displays the screenshot and project documentation; the interactive `.pbix` report must be opened in Power BI Desktop (or published separately to an appropriate Power BI service workspace).

## Skills Demonstrated

Power BI · Power Query · DAX · Data Cleaning · KPI Development · Data Visualization · Business Performance Analysis · Interactive Reporting · Git/GitHub

## Project Status

Core dashboard visuals and slicers have been implemented. Potential refinements include month-level trend aggregation, visual formatting improvements, and additional profitability analysis.

## Disclaimer

This is an educational portfolio project using **synthetic data**. Results and recommendations are illustrative and should not be treated as findings about an actual business.
