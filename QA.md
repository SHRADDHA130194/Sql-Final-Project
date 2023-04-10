What are your risk areas? Identify and describe them.


1.Identifying Primary and Foregin Key.I tried to remove duplicates and all  but still I can not recognise any unique key in all table.


2.Finding relationships in diffrent table of database.

3.Allocating right Data Type.



QA Process:

Describe your QA process and include the SQL queries used to execute it.

1.Check for null values in columns:
```
SELECT 
        COUNT(*) FROM table_name 
WHERE   column_name IS NULL; 
```

2.Check for duplicate rows: 
```
SELECT
         COUNT(*) 
FROM 
(
    SELECT 
            column1, column2,..., COUNT(*) 
    FROM 
            table_name 
    GROUP BY column1, column2, column3, ...
    HAVING COUNT(*) > 1
) AS subquery; 
```
3.Proper Syntax Used.

4 .Cross Check

```
SELECT COUNT(temp) 
FROM    (
        SELECT 
        a.visitid ,b.visitid,a.productsku as temp,units_sold
        FROM all_sessions a
        INNER JOIN analytics b
        ON a.visitid = b.visitid
        where units_sold is not null
    ) tmp
	
SELECT count(productsku) 
FROM sales_by_sku where total_ordered is not null

```

Got same results 306