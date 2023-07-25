Additional questions and answers:
Question 1: 
 There are 454 products available with  a total of 5519 orders (per Sales_Report )
  304  products have orders  
  150  products have no orders at all 


Question 2 and 3:

 StockLevel   vs Restocking LeadTime
The majority of the stock Levels are higher than RestockingLead Time, 
Products  that does not meet the previous statement have a total_ordered of 10 or less




SQL Queries:

SELECT COUNT("SKU")as no_orders FROM sales_report
where total_ordered = 0

SELECT COUNT("SKU")as with_orders FROM sales_report
where total_ordered > 0



SELECT total_ordered, "SKU", "stockLevel", "restockingLeadTime" ,
CASE
	when "stockLevel" < "restockingLeadTime"  then '"watch_item"'
	else 'ok'
END
FROM sales_report
where total_ordered > 0
ORDER BY total_ordered ASC






