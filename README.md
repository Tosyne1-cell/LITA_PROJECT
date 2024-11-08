# LITA_ CAPSTONE PROJECT 1 AND 2
## Project Tittle: Creating reports using

I EXCEL

II SQL

III POWERBi to Initial Sales Data Exploration Report.


[I EXCEL](#i-excel)

[Key Findings](#key-findings)

[Other Interesting Reports](#other-interesting-reports)

[Pivot Table Screenshot](#pivot-table-screenshot)

[Formulas Used](#formulas-used)

[Summary](#summary)

[II SQL](#ii-sql)

[SUMMARY And Conclusion](#summary-and-conclusion)

[III POWERBi](#iii-powerbi)

[Project Scope and Requirements](#project-scope-and-requirements)

[Data Sources and Preparation](#data-sources-and-preparation)

[Dashboard Design and Development](#dashboard-design-and-development)

[Insights and Findings](#insights-and-findings)


# PROJECT1(SALES DATA)


## I EXCEL

### OBJECTIVE
- To Perform an initial exploration of the sales data. Use pivot tables to summarize 
  total sales by product, region, and month.
-To Use Excel formulas to calculate metrics such as average sales per product and 
total revenue by region.
- Create any other interesting report

### Key Findings:

Total Sales by Product:

| Product | Total Sales |
| --- | --- |
| Socks | 912,500 |
| Jacket | 1,050,000 |
| Gloves | 1,587,500|


Average Sales per Product:

| Product | Average Sales |
| --- | --- |
| SOCKS | 122 |
| JACKET | 140 |
| HAT  | 159 |
| GLOVES |200 |
| SHOES| 309 |
| SHIRT | 327 |
| GRAND TOTAL | 212 |

Total Revenue by Region:

| Region | Total Revenue |
| --- | --- |
| North | 1,950,000 |
| South | 4,675,000 |
| East | 2,450,000 |
| West | 2,512,500 |
| GRAND TOTAL | 10,587,500

### Other Interesting Reports:

1. Top 3 Products by Sales: SHOES, SHRIRT, HAT
2. Region with Highest Sales Growth: SOUTH
3. Month with Lowest Sales: SEPTEMBER 175,000

   

Pivot Table Screenshot:

![Screenshot 2024-11-06 080830](https://github.com/user-attachments/assets/40a44d05-f9b0-42a0-b9a6-bede4087772b)


### Formulas Used:

1. =SUM(Sales*Product) (Total Sales by Product)
2. =AVERAGE(TOTAL SALES/UNIT COST) (Average Sales per Product)

### Summary:
This report provides an initial exploration of the sales data, utilizing pivot tables and Excel formulas to summarize key metrics.


## II SQL

### OBJECTIVE: 
 - To retrieve the total sales for each product category.
 - To find the number of sales transactions in each region.
 - To find the highest-selling product by total sales value.
 - Tocalculate total revenue per product.
 - To calculate monthly sales totals for the current year.
 - To find the top 5 customers by total purchase amount.
 - To calculate the percentage of total sales contributed by each region.
 -  To identify products with no sales in the last quarter.


-----LITA CAPSTONE DATA PROJECT 1

```SQL
SELECT * FROM  Customer_Data
```

1. Total sales for each product category
  
  ```SQL
Select [Product], Sum(Sales) AS [Total Sales] From Customer_Data
GROUP BY [Product] Order By [Total Sales] DESC
```

2. Number of Sales Transaction in each region

```SQL
SELECT Region, Count(OrderID) AS [No. of sales trans.] from Customer_Data
GROUP BY Region Order by 2 desc
```

3. HIGHEST SELLING PRODUCT BY TOTAL SALES

```SQL
SELECT TOP 1 [Product], Sales FROM Customer_Data
WHERE Sales = (SELECT MAX(Sales) FROM Customer_Data)
---Showing the total sales made from Shoe
SELECT TOP 1 Product, SUM(Sales) AS TotalSales FROM Customer_Data
GROUP BY Product
```


4. Total Revenue per product

```SQL
     Select [Product], Sum(  Quantity * UnitPrice) as Totalsales
	 From Customer_Data
	 Group By [Product]
```

5. Monthly sales total for 2024

```SQL

Select FORMAT(OrderDate, 'YYYY-MM') AS [MONTH], SUM(Sales) AS [Total Sales]
FROM Customer_Data WHERE Year(OrderDate) = 2024
Group by FORMAT(OrderDate, 'YYYY-MM')
ORDER BY 1
```

6. Top 5 customers by total purchase amount

```SQL

SELECT * FROM Customer_Data
Select TOP 5 Customer_id, Sum (Sales) as [Total Purchase] FROM Customer_Data
GROUP BY Customer_id Order by 2 DESC
```

7. Percentage of Total sale Contributed by Region
--- % = (sales/ Total sales ) * 100

```SQL
SELECT  Region, SUM(Sales) AS Region_Sales,
(SUM (Sales) / (Select Sum(Sales) from Lita_Data )* 100) As [Pecentage%]
FROM Customer_Data GROUP BY Region
```


8. Identify products with no sale in the last quarter---
---Last quarter is July - Sept 2024

```SQL
SELECT DISTINCT Product From Customer_Data
EXCEPT Select Distinct Product from Customer_Data
WHERE OrderDate >= '2024-07-01' AND OrderDate < '2024-10-01'
```

-----Another Alternative with the DATEADD FUNCTION--

```SQL

SELECT DISTINCT Product FROM Customer_Data
WHERE Product NOT IN (
    SELECT Product FROM Customer_Data
    WHERE OrderDate >= DateAdd(Quarter, -1, GetDate() ) 
	)
```
### SUMMARY And Conclusion

At the end i was able to: Get
Total sales by category.
Highest and lowest sales days.
Top-performing products and categories.
The SQL queries provided valuable insights into sales data, highlighting top-selling products, regions, and customers. The analysis also identified products with no sales in the last quarter.




## III POWERBi


### OBJECTIVE:The primary goal of this project was to create an interactive and insightful dashboard that visualizes key sales metrics derived from Excel and SQL databases. This dashboard is intended to provide a quick overview of sales performance, highlight top-performing products, and present a regional breakdown of sales.


### Project Scope and Requirements:

The dashboard needed to include:

Sales Overview: A general overview summarizing total sales, average sales, growth rate, and sales trend over a selected period.
Top-Performing Products: Visual identification of the highest-selling products to focus on top revenue drivers.
Regional Breakdowns: Insight into sales by region, allowing for targeted strategies based on geographic performance.

### Data Sources and Preparation:


Excel Data: Cleaned and organized to ensure compatibility with SQL datasets. Key metrics like product IDs, sales quantities, revenue, and region-specific data were stored.

SQL Database: Aggregated data from transactional tables, including sales figures, product information, and regional identifiers. Queries were written to pull and join relevant datasets to structure the information for visualization.

Data Transformation: Excel and SQL data were combined using transformations to remove redundancies, standardize data formats, and prepare data tables required for each dashboard element.

### Dashboard Design and Development:

Tools: Power BI was chosen for its powerful integration capabilities with both Excel and SQL and its robust visualization options.


PowerBi Screenshot:

![Screenshot 2024-11-07 205739](https://github.com/user-attachments/assets/05282a4d-1986-47b7-8efd-78c6a58dbfed)



### Insights and Findings:

The dashboard successfully integrates Excel and SQL data to provide an at-a-glance summary of key sales insights. Moving forward, it is recommended to automate data updates and consider adding additional filters for seasonality analysis. Regular feedback from users will also help to fine-tune visualizations for enhanced decision-making.



# PROJECT 2 (CUSTOMER DATA)

**Excel Analysis Report: Customer Subscription Data**

**Objective:**
The aim of this analysis is to explore customer subscription patterns, calculate the average subscription duration, identify the most popular subscription types, and generate additional insightful reports from the available customer data using Excel.

---

**Analysis Process:**

1. **Data Preparation**:
   - Data was cleaned to ensure accuracy, consistency, and compatibility for pivot table analysis.
   - Customer records with incomplete or inconsistent subscription data were corrected or excluded.

2. **Pivot Table Analysis for Subscription Patterns**:
   - **Subscription Frequency**: Created pivot tables to observe how often customers renew their subscriptions and the timing of renewals. This helped identify any seasonal or monthly peaks in subscription renewals.
   - **Customer Segmentation by Subscription Length**: Grouped customers based on the duration of their subscriptions ( monthly, quarterly, annually) to see which durations were most popular.

3. **Average Subscription Duration**:
   - Calculated the average duration by using Excel’s `AVERAGE` function on the "Subscription Duration" column.
   - This revealed insights into typical customer retention periods and helped identify if shorter or longer durations were more prevalent.

4. **Popular Subscription Types**:
   - Analyzed subscription types  	Basic, Premium, Standard to determine which options are most popular.
   - Pivot tables were used to calculate the number of customers per subscription type, showing clear preferences and highlighting which packages drive the most customer interest.
  
     ![Screenshot 2024-11-07 210750](https://github.com/user-attachments/assets/3740ef1a-e65e-419f-9867-daed45a5721f)



**Conclusion and Recommendations:**

The Excel analysis provided valuable insights into subscription patterns, customer preferences, and revenue drivers. To enhance customer retention, targeted offers around the average subscription duration and popular renewal periods are recommended. Additionally, expanding Premium offerings could further boost revenue, given its popularity. 


**SQL Query Report: Subscription Data Analysis** To retrieve the total number of customers from each region.
o find the most popular subscription type by the number of customers.
o find customers who canceled their subscription within 6 months.
o calculate the average subscription duration for all customers.
o find customers with subscriptions longer than 12 months.
o calculate total revenue by subscription type.
o find the top 3 regions by subscription cancellations.
o find the total number of active and canceled subscriptions



![Screenshot 2024-11-07 215009](https://github.com/user-attachments/assets/354fe943-c5ce-412b-bfd4-afc3a1dc83f7)


**Summary**:
The queries provide insights into customer distribution, popular subscriptions, churn patterns, 
and revenue. This data is crucial for improving customer retention and identifying revenue opportunities.



**Power BI Dashboard Overview: Customer Segments, Cancellations, and Subscription Trends**

**Objective**: To create an interactive Power BI dashboard that provides insights into key customer segments, cancellation rates, and subscription trends. This dashboard allows users to explore data with slicers for dynamic filtering.

**Dashboard Components/Visuals**
   - Donut chart
   - Stacked column chart
   - Cards
   - Slicer
   - Table

     ![Screenshot 2024-11-07 211157](https://github.com/user-attachments/assets/6afa9675-d0b3-4eb5-9175-81e362f9be33)


   ### Conclusion and Recommendations:

The Power BI dashboard offers a comprehensive, interactive view of customer segmentation, cancellation patterns, and subscription trends. For actionable insights




