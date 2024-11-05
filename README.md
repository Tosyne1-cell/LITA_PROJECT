# LITA_PROJECT
## Project Tittle: Creating reports using excel
Initial Sales Data Exploration Report

Summary:

This report provides an initial exploration of the sales data, utilizing pivot tables and Excel formulas to summarize key metrics.

Key Findings:

Total Sales by Product:

| Product | Total Sales |
| --- | --- |
| Socks | 912,500 |
| Jacket | 1,050,000 |
| Gloves | 1,587,500




Average Sales per Product:

| Product | Average Sales |
| --- | --- |
| Product A | $1,431 |
| Product B | $1,019 |
| Product C | $685 |

Total Revenue by Region:

| Region | Total Revenue |
| --- | --- |
| North | 1,950,000 |
| South | 4,675,000 |
| East | 2,450,000 |
| West | 2,512,500 |
| GRAND TOTAL | 10,587,500

Other Interesting Reports:

1. Top 3 Products by Sales: Product A, Product B, Product C
2. Region with Highest Sales Growth: East (25% MoM)
3. Month with Lowest Sales: June ($8,402)

Pivot Table Screenshot:

[Insert Pivot Table Screenshot]

Formulas Used:

1. =SUMIFS(Sales, Product, "Product A") (Total Sales by Product)
2. =AVERAGEIFS(Sales, Product, "Product A") (Average Sales per Product)
3. =SUMIFS(Revenue, Region, "North") (Total Revenue by Region)


