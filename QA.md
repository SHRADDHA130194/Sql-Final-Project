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

4 .