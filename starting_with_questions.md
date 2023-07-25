Answer the following questions and provide the SQL queries used to find the answer.


Here is one more time and for the 3rd time same information as per your request:

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?*
Question 1: Highest level of transaction revenue (per All_sessions table)
Country – United States
City – Atlanta

SELECT country, city, "totalTransactionRevenue" FROM all_sessions
WHERE "totalTransactionRevenue" IS NOT NULL and country != 'NULL' and city != 'NULL'
ORDER BY "totalTransactionRevenue" DESC, country, city
LIMIT 3


**Question 2: What is the average number of products ordered from visitors in each city and country?**
Question 2: Average products ordered from visitors per country and city (top 3)
  Top 3 
Brano, Czechia 
Riyadh, Saudi Arabia
Rexburg, United States
 From 454 different products and 5518 orders the average products ordered overall  is 12


SELECT AVG(total_ordered)average,
FROM sales_report
ORDER BY  average DESC

SELECT AVG(total_ordered)average, als.country, als.city
FROM sales_report
JOIN all_sessions als
ON als."SKU" = sales_report."SKU"
WHERE country != 'NULL' and city != 'NULL'
GROUP BY als.country, als. city
ORDER BY  average DESC, als.country, als.city, 


**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**
**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**

Question 3 and 4: Pattern in product categories of products ordered per country and city and Top selling product per country and city

 More analysis  or data is required to define potential pattern  by city 
  The current  information shows that :	The product ordered the most  is "Ballpoint LED Light Pen“  from Home/Office category
    United States and Germany have the most visitors for this  product


SELECT sr.total_ordered, sr."SKU", sr."name" FROM sales_report sr
ORDER BY total_ordered DESC
LIMIT 3


SELECT "v2ProductCategory", "v2ProductName", country FROM all_sessions
where "v2ProductName" = 'Ballpoint LED Light Pen'

SELECT country, COUNT("fullVisitorId") FROM all_sessions
where "v2ProductName" = 'Ballpoint LED Light Pen'
GROUP BY country
HAVING COUNT("fullVisitorId")>0
ORDER BY COUNT("fullVisitorId")DESC


**Question 5: Can we summarize the impact of revenue generated from each city/country?**

Question 5: Impact of revenue (per city and country)

  From all totaltransactions available where the country and city is define:
	86% of the total transactions revenue  is from United States 
	14% of the total transactions revenue is from Israel, Australia, Canada and Switzerland
	The top contributing cities from United States are Sunnyvale, Atlanta  and San Francisco
	The top contributing cities for the 14% are Tel Aviv-Yafo, Sydney, Toronto and Zurich


SELECT SUM("totalTransactionRevenue"), country FROM all_sessions 
WHERE city != 'NULL' and country != 'NULL' 
and "totalTransactionRevenue" IS NOT NULL
GROUP BY country
ORDER BY SUM("totalTransactionRevenue") DESC

SELECT SUM("totalTransactionRevenue"), country, city FROM all_sessions 
WHERE city != 'NULL' and country != 'NULL' 
and "totalTransactionRevenue" IS NOT NULL
GROUP BY country, city
ORDER BY SUM("totalTransactionRevenue") DESC








