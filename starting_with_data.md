Question 1: 
Which products needs to restock?


SQL Queries:
```
-- Ordered Product which is low in stocklevel.

SELECT
		orderedquantity,productsku,total_ordered,name,stocklevel
FROM  	
		products p 
JOIN
		sales_by_sku s
ON		
		p.sku = s.productsku
WHERE 
		total_ordered > stocklevel
ORDER BY s.total_ordered DESC , p.orderedquantity DESC
```

Answer: 

Android Infant Short Sleeve Tee Pewter


 Youth Baseball Raglan Heather/Black







Question 2: 

How to Classify products in three categories?

SQL Queries:

```
-- Clasification of products in three categories

SELECT 
		productsku, total_ordered, name, stocklevel,
CASE
   WHEN total_ordered > 400 THEN 'High Demand'
   WHEN total_ordered > 50 THEN  'In Demand'
   ELSE 'Not In Demand' 
END AS Product_Clasification
FROM public.sales_report
ORDER BY stocklevel DESC

```
Answer:

Not In Demand


In Demand


High In Demand

Question 3: 

How much time spend by customer who buys product?

SQL Queries:
```
--Time spend on site by customer who buy something
SELECT 
		a2.timeonsite, a1.fullvisitorid,revenue 
FROM 
		analytics a2
JOIN 
		all_sessions a1 ON a1.visitid = a2.visitid 
WHERE 
		revenue is not NULL
GROUP BY a1.fullvisitorid,a2.timeonsite,revenue
ORDER BY revenue DESC,a2.timeonsite
```
Answer:

timeonsite
264

800

943

392

539

483

777

1222

1222

1169

483

214

800

1222


Question 4: 

How time spent on site is affects total revenue?

SQL Queries:
```
-- How time spent on site is affects total revenue.
SELECT visitid,visitnumber,timeonsite,Sum(revenue)
OVER  
 		(PARTITION BY visitid
 		ORDER BY visitid) 
as Total_Revenue
FROM analytics
WHERE revenue is not null 
```

Answer:

Increase in time spend increase revenue



Question 5: 

Which Is highest selling Product?


SQL Queries:
```
--highest selling product

SELECT total_ordered,country,name
FROM all_sessions a
JOIN sales_report s 
ON a.productsku = s.productsku
WHERE productrevenue is not null

```


Answer:

 Cam Indoor Security Camera - USA

2.5_highest SellingProduct.csv