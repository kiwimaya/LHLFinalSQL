Below information can also be found in the attch powerpoint presentation.

What are your risk areas? 

- Assumptions on the data were made with out the option to contact the database creator

- Database provieded seems to have a lot of subjetivity or lack of standards in its contents

QA Process:

-- Understanding the accuracy and completeness of the data, verifying data types are compatible with each other,  understanding the relations between tables
-- Comparing counts with the data source files
-- Random  searching of values


Query Examples for quality testing:

Unit Test Examples
--count in both tables  is 5511 SKU

SELECT COUNT(p."SKU"), COUNT(als."SKU") FROM products p
JOIN all_sessions als
ON als."SKU" = p."SKU"
WHERE als.city != 'NULL' and als.country != 'NULL’


 Comparing counts with the data source files
Random  searching of values

SELECT DISTINCT als."SKU", als.country, sr.total_ordered, sr.name from all_sessions als
JOIN sales_report sr
ON als."SKU" = sr."SKU"
WHERE country != 'NULL' and city != 'NULL' and country = 'United States'
ORDER BY als.country, total_ordered DESC






