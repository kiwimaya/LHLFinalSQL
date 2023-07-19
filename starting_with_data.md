Question 1: 

![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/14097f78-4a2a-4e16-b528-5557c927c012)

SELECT country, city, "totalTransactionRevenue" FROM all_sessions
WHERE "totalTransactionRevenue" IS NOT NULL and country != 'NULL' and city != 'NULL'
ORDER BY "totalTransactionRevenue" DESC, country, city
LIMIT 3
![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/ecc4fc74-f442-4b93-b33c-4708900ef541)



Question 2: 


![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/a0236e22-4e08-428a-9013-99daf694d962)


SQL Queries:

SELECT AVG(total_ordered)average,
FROM sales_report
ORDER BY  average DESC
![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/172d0410-0656-4541-b2da-daae7575f2a8)


Question 3 & 4:


![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/d9e50f07-fd03-4844-83a5-678cbd575e24)




SQL Queries: 
SELECT sr.total_ordered, sr."SKU", sr."name" FROM sales_report sr
ORDER BY total_ordered DESC
LIMIT 3


SELECT "v2ProductCategory", "v2ProductName", country FROM all_sessions
where "v2ProductName" = 'Ballpoint LED Light Pen'
![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/4e026329-be24-43d8-a71d-f19de22ab26b)

SELECT country, COUNT("fullVisitorId") FROM all_sessions
where "v2ProductName" = 'Ballpoint LED Light Pen'
GROUP BY country
HAVING COUNT("fullVisitorId")>0
ORDER BY COUNT("fullVisitorId")DESC
![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/f023b9b5-3de6-4aca-bae6-c6c145657728)





Question 5: 


![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/100f3679-6b45-4128-9f4e-aef3b3e376cd)

SELECT SUM("totalTransactionRevenue"), country, city FROM all_sessions 
WHERE city != 'NULL' and country != 'NULL' 
and "totalTransactionRevenue" IS NOT NULL
GROUP BY country, city
ORDER BY SUM("totalTransactionRevenue") DESC
![image](https://github.com/kiwimaya/LHLFinalSQL/assets/134563688/4a199110-3f61-4742-a53c-b9772dbb4157)




