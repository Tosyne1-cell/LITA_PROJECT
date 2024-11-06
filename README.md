# LITA_PROJECT
## Project Tittle: Creating reports using

I EXCEL

II SQL

III POWERBi to Initial Sales Data Exploration Report.



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

5. Monthly sales total for 2024-

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
### SUMMARY

At the end i was able to: Get
Total sales by category.
Highest and lowest sales days.
Top-performing products and categories.

### Conclusion:

The SQL queries provided valuable insights into sales data, highlighting top-selling products, regions, and customers. The analysis also identified products with no sales in the last quarter.




## III POWERBi


### OBJECTIVE:

- To Create a dashboard that visualizes the insights found in Excel and SQL.
-  The dashboard should include:
   A sales overview,
  Top-performing products, and 
  Regional breakdowns
