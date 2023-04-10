Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
```
SELECT 
        city,country,max(totaltransactionrevenue) 
AS
        highest_transaction_revenues 
FROM
        all_sessions 
WHERE
        totaltransactionrevenue is not NULL
GROUP BY city,country  
ORDER BY max(totaltransactionrevenue) DESC , city , country

```

Answer:


Starting_with_Ans1.csv

Atlanta and Sunnyvale from United State and Tel Aviv-Yafo from Israel



**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:

```
SELECT 
      city,country,Round(avg(units_sold),2) AS avgproductsordered
From
     all_sessions as s
INNER JOIN
     analytics as a
     ON 
     a.visitid = s.visitid
WHERE
     units_sold is not null
GROUP BY city,country  
ORDER BY Round(avg(units_sold),2) DESC
```

Answer:

Starting_with_Ans2.csv




**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
```
SELECT
         city,country,Round(avg(units_sold),2) as avgproductsordered, v2productcategory
FROM
         all_sessions as s
INNER JOIN
         analytics as a 
ON 
        a.visitid = s.visitid
WHERE 
        units_sold is not NULL
GROUP BY  city,country, v2productcategory
ORDER by Round(avg(units_sold),2) DESC
```
Answer:
Starting_with_Ans3.csv

Mountain View, United States has highest avgproductsordered in "Home/Spring Sale!/".
United State hase maximum product orders.



**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
```
SELECT
        city,country,v2productname, Round(max(units_sold),2) AS                                                  avgproductsordered
FROM
         all_sessions as s
INNER JOIN
         analytics as a on a.visitid = s.visitid
WHERE
         units_sold is not null
GROUP BY city,country, v2productname
ORDER by Round(max(units_sold),2) desc

```


Answer:
Starting_with_Ans4.csv

Grip Highlighter Pen 3 Pack is highest selling product in USA. 




**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
```
SELECT
         city,country, sum(COALESCE(revenue, 0)) AS Revenue
FROM
        all_sessions as s
INNER JOIN
         analytics as a on a.visitid = s.visitid
WHERE
         units_sold is not null
GROUP BY city,country
ORDER by sum(COALESCE(revenue, 0)) DESC

```

Answer:


Starting_with_Ans5.csv


United States and New York city has highest totalproductrevenue. 
Isarael and Switzerland is second and third country respectively.





