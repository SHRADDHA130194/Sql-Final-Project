What issues will you address by cleaning the data?

1.Changing format.

2.Removing duplicates without unique id.

3.Finding Missing Values.





Queries:
Below, provide the SQL queries you used to clean your data.

Step 1: 

Find all null columns and delete it.

```

SELECT 
        *
 FROM tablename 
WHERE columnname IS NOT NULL
ALTER TABLE  
        tablename
 DROP columnname
```

Step 2:
Remove Duplicates.

```
CRETE TABLE TEMP
AS
SELECT
        DISTINCT * 
FROM tablename.
```

```
DROP table name

```

RENAME TEMP AS tablename



Step 3: 

Put null value for incorrect syntext
```
UPDATE 
        all_sessions
SET 
        city = NULL 
WHERE
         city = 'not available in demo dataset' or city = '(not set)'
```
step 4:

Chage  format
```
UPDATE
         table_name 
SET
         date_column = TO_DATE(varchar_column, 'YYYYMMDD');

```
UPDATE 
        all_sessions
SET 
        price = price/1000000 

```


