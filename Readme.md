\# Pharma Sales SQL Analysis





**Project Overview -** 



This project analyzes two years of simulated pharmacy sales data using MySQL extension in Visual studio Code.

It demonstrates SQL skills for business analytics, including aggregations, window functions,

date operations, and performance optimization.





**Dataset**

pharma\_sales\_2023\_2024.csv — synthetic dataset with sales from 2023–2024.

Columns: sale\_date, category, medicine\_name, amount





**Skills Used**



SQL Aggregations (SUM, AVG, COUNT)

Window Functions (RANK, OVER)

Subqueries

Date Functions



**Key Insights**



Top-selling medicine in each category

Monthly and yearly sales trends

7-Year moving average 

Percent change per month





**Sample Queries**





select date\_format(sale\_date, '%Y-%m') as month, category, sum(amount) as Totalsales 

from dailysales 

group by month, category

order by month;





with monthly\_sales as (

&nbsp;   select DATE\_FORMAT(sale\_date, '%Y-%m') as months, category, sum(amount) as Totalsales

&nbsp;   from dailysales

&nbsp;   group by months,category )

&nbsp;   select months , category , Totalsales, 

&nbsp;   lag(Totalsales) OVER (partition by category ORDER BY months) as prev\_month\_sales,

&nbsp;   round((Totalsales - lag(Totalsales)Over(partition by category order by months))/ LAG(Totalsales) over(partition by category order by    months)\*100,2) as pct\_change 

&nbsp;   from monthly\_sales;











