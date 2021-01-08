# SQL Programming Notes

## Contents
* [CREATE TABLE](#CREATE_TABLE)
* [SELECT](#SELECT)
* [SELECT DISTINCT](#SELECT_DISTINCT)
* [UNION](#UNION)
* [INSERT INTO](#INSERT_INTO) 
* [UPDATE](#UPDATE)
* [DELETE](#DELETE)
* [JOIN](#JOIN)
* [WHERE](#WHERE)
* [ORDER BY](#ORDER_BY)
* [GROUP BY](#GROUP_BY)
* [BETWEEN](#BETWEEN)
* [IN](#IN)
* [LIKE](#LIKE)
* [ANY](#ANY)
* [ALL](#ALL)
* [CASE](#CASE)

## CREATE_TABLE  
**Syntax**
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
)
```

【Example】 
```sql
CREATE TABLE Summary (
    ID int,
    class varchar(255),
    price int,
    quantity int
)
```
> | ID | class | price | quantity |
> | ---------- | ----------- | ---------- | ----------- | 

Back to [Contents](#Contents)

## SELECT  
The `SELECT` statement is used to select data from a database.  
<br>
**Syntax** 
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1
GROUP BY column_name(s) HAVING condition2  
ORDER BY column_name(s) ASC|DESC
```

(i) Create the Table Using Another Table   
A copy of an existing table can be created using `CREATE TABLE`.  
**Syntax**  
```sql
CREATE TABLE new_table_name AS
    SELECT column1, column2,...
    FROM existing_table_name
    WHERE condition
```

【Example】  
There is an existing table called "OrderList" : 
| ID | class | price | quantity |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | A | 500 | 20 |
| 2 | B | 350 | 10 |
| 3 | C | 400 | 15 |
| 4 | A | 200 | 30 |

(1) Select two columns from "OrderList" :
```sql
CREATE TABLE New_OrderList AS
    SELECT ID, class
    FROM OrderList
```
> | ID | class | 
> | ---------- | ----------- |  
> | 1 | A |
> | 2 | B | 
> | 3 | C | 
> | 4 | A | 

(2) Select three columns from "OrderList" and create an new column from original "price" column :
```sql
CREATE TABLE New_OrderPrice AS 
    SELECT ID, class, price, price+1 NewPrice 
    FROM OrderList
```
> | ID | class | price | NewPrice |
> | ---------- | ----------- | ---------- | ----------- | 
> | 1 | A | 500 | 501 |
> | 2 | B | 350 | 351 |
> | 3 | C | 400 | 401 |
> | 4 | A | 200 | 201 |

Back to [Contents](#Contents)
<br>

## SELECT_DISTINCT 
The `SELECT DISTINCT` statement is used to return only distinct (different) values.
```sql
CREATE TABLE Class AS
    SELECT DISTINCT class
    FROM OrderList
```
> | class | 
> | ---------- |  
> | A |
> | B | 
> | C | 

Back to [Contents](#Contents)
<br>

## UNION  
The `UNION` operator is used to combine the result-set of two or more `SELECT` statements. Each `SELECT` statement within UNION must satisfy the following conditions : 
- Each `SELECT` statement have the same number of columns； 
- The columns in each `SELECT` statement must also be in the same order；
- The columns must also have similar data types.  

**Syntax**  
```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2
```

【Example】   
There are two existing tables :   
Table1 
| ID | name | height | weight |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | Jack | 180 | 75 |
| 2 | Andy | 175 | 65 |
| 3 | Mark | 183 | 90 |
  
Table2 
| ID | name | height | weight |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | Tom | 172 | 68 |
| 2 | Ellen | 167 | 55 |
| 3 | Jack | 180 | 75 |

(1) The `UNION` operator returns the names (only distinct values) from both the "Table1" and the "Table2" table : 
```sql
SELECT name FROM Table1
UNION
SELECT name FROM table2
```
> | name |
> | ---------- |
> | Jack |
> | Andy |
> | Mark |  
> | Tom | 
> | Ellen | 

(2) Use `UNION ALL` to also select duplicate values : 
```sql
SELECT name FROM Table1
UNION ALL  
SELECT name FROM table2
```
> | name |
> | ---------- |
> | Jack |
> | Andy |
> | Mark |  
> | Tom | 
> | Ellen | 
> | Jack | 

Back to [Contents](#Contents)
<br>

## INSERT_INTO
The `INSERT INTO` statement is used to insert new records in a table.  
<br>
**Syntax**  
```sql
INSERT INTO table_name(column1, column2, column3, ...)
VALUES (value1, value2, value3, ...)
```

【Example】   
There is an existing table called "MyTable" : 
| ID | name | age | 
| ---------- | ----------- | ---------- | 
| 1 | Tom | 28 |
| 2 | Bob | 19 |

Insert a new record in "MyTable" :
```sql
INSERT INTO MyTable 
VALUES (3, 'Amy', 16)
```
> | ID | name | age | 
> | ---------- | ----------- | ---------- | 
> | 1 | Tom | 28 |
> | 2 | Bob | 19 |
> | 3 | Amy | 16 | 
```sql
INSERT INTO MyTable(ID,name) 
VALUES (4, 'Andy')
```
> | ID | name | age | 
> | ---------- | ----------- | ---------- | 
> | 1 | Tom | 28 |
> | 2 | Bob | 19 |
> | 3 | Amy | 16 | 
> | 4 | Andy | null | 

Back to [Contents](#Contents)
<br>

## UPDATE  
The `UPDATE` statement is used to modify the existing records in a table.  
<br>
**Syntax**  
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition
```
Note : if we omit the `WHERE` clause, all records will be updated.  

【Example】   
There is an existing table called "MyTable" : 
| ID | name | age | 
| ---------- | ----------- | ---------- | 
| 1 | Tom | 28 |
| 2 | Bob | 19 |
| 3 | Amy | 19 |

Update the age to 50 where name is "Bob"
```sql
UPDATE MyTable
SET age = 50
WHERE name = 'Bob' 
```
> | ID | name | age | 
> | ---------- | ----------- | ---------- | 
> | 1 | Tom | 28 |
> | 2 | Bob | 50 |
> | 3 | Amy | 19 |

Back to [Contents](#Contents)
<br>

## DELETE  
The `DELETE` statement is used to delete existing records in a table.  
<br>
**Syntax**  
```sql
DELETE FROM table_name 
WHERE condition
```
Note : The `WHERE` clause specifies which record(s) should be deleted. If we omit the `WHERE` clause, all records in the table will be deleted.

【Example】   
There is an existing table called "MyTable" : 
| ID | name | age | 
| ---------- | ----------- | ---------- | 
| 1 | Tom | 28 |
| 2 | Bob | 19 |
| 3 | Amy | 19 |

Delete the data with age > 20 : 
```sql
DELETE FROM MyTable
WHERE age > 20 
```
> | ID | name | age | 
> | ---------- | ----------- | ---------- | 
> | 2 | Bob | 19 |
> | 3 | Amy | 19 |

Back to [Contents](#Contents)
<br>

## JOIN  
A `JOIN` clause is used to combine rows from two or more tables, based on a related column between them.
![IMAGE](/SQL%20Syntax/SQL%20JOIN.png)
<br>
**Syntax about INNER JOIN**  
```sql
SELECT table_1.column_1, table_1.column_2, table_2.column_1, table_2.column_2, ...
FROM table_1
INNER JOIN table_2 
ON table_1.key_column = table_2.key_column
```

【Example】   
We have the following two tables :   
Table1 
| ID | name | height | weight |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | Jack | 180 | 75 |
| 2 | Andy | 175 | 65 |
| 3 | Mark | 183 | 90 |
| 4 | Rose | 163 | 45 |
  
Table2 
| ID | sex | 
| ---------- | ----------- | 
| 2 | M | 
| 3 | M | 
| 4 | F |
| 5 | F |

(1) The `INNER JOIN` keyword selects all rows from both the tables as long as the condition satisfies. 
```sql
SELECT Table1.ID, Table1.name, Table2.sex
FROM Table1  
INNER JOIN Table2 
ON Table1.ID = Table2.ID 
```
> | ID | name | sex | 
> | ---------- | ----------- | ----------- | 
> | 2 | Andy | M |
> | 3 | Mark | M |
> | 4 | Rose | F |

```sql
SELECT Table1.ID, Table1.name, Table2.sex
FROM Table1  
INNER JOIN Table2 
ON Table1.ID = Table2.ID 
WHERE Table1.name = 'Rose'
```
> | ID | name | sex | 
> | ---------- | ----------- | ----------- | 
> | 4 | Rose | F |

(2) The `LEFT JOIN` returns all the rows of the table on the left side of the join and matching rows for the table on the right side of join. The rows for which there is no matching row on right side, the result-set will contain null. (`LEFT JOIN` is also known as `LEFT OUTER JOIN`)  
```sql
SELECT Table1.ID, Table1.name, Table1.height, Table2.sex
FROM Table1  
LEFT JOIN Table2 
ON Table1.ID = Table2.ID 
```
> | ID | name | height | sex | 
> | ---------- | ----------- | ----------- | ----------- | 
> | 1 | Jack | 180 | NULL |
> | 2 | Andy | 175 | M |
> | 3 | Mark | 183 | M |
> | 4 | Rose | 163 | F |

(3) The `FULL JOIN` creates the result-set by combining result of both `LEFT JOIN` and `RIGHT JOIN`. The result-set will contain all the rows from both the tables. The rows for which there is no matching, the result-set will contain NULL values.
```sql
SELECT Table1.name, Table1.height, Table2.sex
FROM Table1  
FULL JOIN Table2 
ON Table1.ID = Table2.ID 
```
> | name | height | sex | 
> | ---------- | ----------- | ----------- | 
> | Jack | 180 | NULL |
> | Andy | 175 | M |
> | Mark | 183 | M |
> | Rose | 163 | F |
> | NULL | NULL | F |

Back to [Contents](#Contents)
<br>

## WHERE 
The `WHERE` clause is used to extract only those records that fulfill a specified condition.  
<br>
**Syntax**  
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
```

【Example】   
There is an existing table called "OrderList" : 
| ID | class | price | quantity |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | A | 500 | 20 |
| 2 | B | 350 | 10 |
| 3 | C | 400 | 15 |
| 4 | D | 200 | 30 |

Select all data with price is greater than 350 and quantity is less than 20, in the "OrderList" table : 
```sql
SELECT *
FROM OrderList
WHERE price>350 AND quantity<20
```
> | ID | class | price | quantity |
> | ---------- | ----------- | ---------- | ----------- | 
> | 3 | C | 400 | 15 |

Back to [Contents](#Contents)
<br>

## ORDER_BY 
The `ORDER BY` keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.
<br>
**Syntax**  
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC
```

【Example】  
There is an existing table called "OrderList" : 
| ID | class | price | quantity |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | A | 500 | 30 |
| 2 | B | 350 | 10 |
| 3 | C | 400 | 15 |
| 4 | D | 200 | 30 |

Select all data from the "OrderList" table, sorted descending by the "quantity" column:
```sql
SELECT *
FROM OrderList
ORDER BY quantity DESC, price ASC
```
> | ID | class | price | quantity |
> | ---------- | ----------- | ---------- | ----------- | 
> | 4 | D | 200 | 30 | 
> | 1 | A | 500 | 30 |
> | 3 | C | 400 | 15 |
> | 2 | B | 350 | 10 |

Back to [Contents](#Contents)
<br>

## GROUP_BY
The `GROUP BY` statement groups rows that have the same values into summary rows. The `GROUP BY` statement is often used with aggregate functions (COUNT, MAX, MIN, SUM, AVG) to group the result-set by one or more columns.   
<br>
**Syntax**  
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s)
```

【Example】  
There is an existing table called "OrderList" : 
| ID | class | price | quantity |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | A | 500 | 30 |
| 2 | B | 350 | 10 |
| 3 | C | 400 | 15 |
| 4 | D | 200 | 30 |
| 5 | A | 400 | 50 |
| 6 | B | 600 | 40 |
| 7 | C | 500 | 20 |
| 8 | A | 300 | 30 |

(1) The following SQL statement lists the number of class, the average of price, the summation of quantity in each class :
```sql
SELECT class, COUNT(ID) count, AVG(price) average_price, SUM(quantity) total_quantity 
FROM Customers
GROUP BY class
```
> | class | count | average_price | total_quantity |
> | ---------- | ----------- | ---------- | ----------- | 
> | A | 3 | 400 | 110 |
> | B | 2 | 475 | 50 |
> | C | 2 | 450 | 35 |
> | D | 1 | 200 | 30 |

(2) The following SQL statement lists the number of class, the average of price, the summation of quantity in each class. And only include average price with more than 400 :
```sql
SELECT class, COUNT(ID) count, AVG(price) average_price, SUM(quantity) total_quantity 
FROM Customers
GROUP BY class
HAVING average_price > 400
```
> | class | count | average_price | total_quantity |
> | ---------- | ----------- | ---------- | ----------- | 
> | B | 2 | 475 | 50 |
> | C | 2 | 450 | 35 |

Back to [Contents](#Contents)
<br>

## BETWEEN
The `BETWEEN` operator selects values within a given range (begin and end values are included).   
<br>
**Syntax**  
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2
```
  
【Example】   
There is an existing table called "MyTable" : 
| ID | name | age | 
| ---------- | ----------- | ---------- | 
| 1 | Tom | 31 |
| 2 | Bob | 21 |
| 3 | Amy | 28 |
| 4 | Ken | 39 |
| 5 | Vic | 30 |

Select all names with a age BETWEEN 21 and 30 :  
```sql
SELECT *
FROM MyTable
WHERE age BETWEEN 21 AND 30
```
> | ID | name | age | 
> | ---------- | ----------- | ----------- |   
> | 2 | Bob | 21 |
> | 3 | Amy | 28 |
> | 5 | Vic | 30 |

Back to [Contents](#Contents)
<br>

## IN  
The `IN` operator allows us to specify multiple values in a `WHERE` clause.  
<br>
**Syntax**  
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...)
```

【Example】   
There is an existing table called "MyTable" : 
| ID | name | age | location | 
| ---------- | ----------- | ---------- | ---------- | 
| 1 | Tom | 31 | Taipei |
| 2 | Bob | 21 | Tainan |
| 3 | Amy | 28 | Hsinchu |
| 4 | Ken | 39 | Taipei |
| 5 | Patty | 30 | Kaohsiung  |  

Select all names that are located in "Taipei" or "Kaohsiung" :
```sql
SELECT * 
FROM MyTable
WHERE location IN ('Taipei', 'Kaohsiung')
```
> | ID | name | age | location | 
> | ---------- | ----------- | ---------- | ---------- | 
> | 1 | Tom | 31 | Taipei |
> | 4 | Ken | 39 | Taipei |
> | 5 | Patty | 30 | Kaohsiung  |  

Select all names that are not located in "Taipei" or "Kaohsiung" :
```sql
SELECT * 
FROM MyTable
WHERE location NOT IN ('Taipei', 'Kaohsiung')
```
> | ID | name | age | location | 
> | ---------- | ----------- | ---------- | ---------- | 
> | 2 | Bob | 21 | Tainan |
> | 3 | Amy | 28 | Hsinchu |

Back to [Contents](#Contents)
<br>

## LIKE
The `LIKE` operator is used in a 'WHERE' clause to search for a specified pattern in a column.
The following examples show different LIKE operators with '%' and '_' wildcards : 
| LIKE Operator | Description |  
| ---------- | ----------- | 
| LIKE 'a%' | Finds any values that start with "a" | 
| LIKE 'a%' | Finds any values that end with "a" |
| LIKE '_b%' | Finds any values that have "b" in the second position |
| LIKE 'a%z' | Finds any values that start with "a" and ends with "z" |
| LIKE 'a_%' | Finds any values that start with "a" and are at least 2 characters in length |

【Example】   
There is an existing table called "MyTable" : 
| ID | name | age | location | 
| ---------- | ----------- | ---------- | ---------- | 
| 1 | Tom | 31 | Taipei |
| 2 | Bob | 21 | Tainan |
| 3 | Amy | 28 | Hsinchu |
| 4 | Ken | 39 | Taipei |
| 5 | Patty | 30 | Kaohsiung  |  

Select all names that are located in cuty with name starting with "T" :
```sql
SELECT * 
FROM MyTable
WHERE location LIKE 'T%'
```
> | ID | name | age | location | 
> | ---------- | ----------- | ---------- | ---------- | 
> | 1 | Tom | 31 | Taipei |
> | 2 | Bob | 21 | Tainan |
> | 4 | Ken | 39 | Taipei |

Back to [Contents](#Contents)
<br>

## ANY  
The `ANY` operator returns true if any of the subquery values meet the condition.   
<br>
**Syntax**  
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY
(SELECT column_name FROM table_name WHERE condition)
```
Note : The operator must be a standard comparison operator (=, <>, !=, >, >=, <, or <=). 

【Example】   
We have the following two tables :   
Table1 
| ID | name | height | weight |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | Jack | 180 | 75 |
| 2 | Andy | 175 | 65 |
| 3 | Mark | 183 | 90 |
| 4 | Rose | 163 | 45 |
| 5 | Tom | 172 | 70 |
  
Table2 
| ID | score | 
| ---------- | ----------- | 
| 1 | 120 |
| 2 | 115 | 
| 3 | 150 | 
| 4 | 135 |
| 5 | 140 |

```sql
SELECT *
FROM Table1 
WHERE ID = ANY
(SELECT ID FROM Table2 WHERE score >= 135)
```
> | ID | name | height | weight |
> | ---------- | ----------- | ---------- | ----------- | 
> | 3 | Mark | 183 | 90 |
> | 4 | Rose | 163 | 45 |
> | 5 | Tom | 172 | 70 |

Back to [Contents](#Contents)
<br>

## ALL  
The `ALL` operator returns true if all of the subquery values meet the condition.   
<br>
**Syntax**  
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ALL
(SELECT column_name FROM table_name WHERE condition)
```
Note : The operator must be a standard comparison operator (=, <>, !=, >, >=, <, or <=). 

【Example】   
We have the following two tables :   
Table1 
| ID | name | height | weight |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | Jack | 180 | 75 |
| 2 | Andy | 175 | 65 |
| 3 | Mark | 183 | 90 |
| 4 | Rose | 163 | 45 |
| 5 | Tom | 172 | 70 |
  
Table2 
| ID | score | 
| ---------- | ----------- | 
| 1 | 120 |
| 2 | 115 | 
| 3 | 150 | 
| 4 | 135 |
| 5 | 140 |

```sql
SELECT *
FROM Table1 
WHERE ID = ALL
(SELECT ID FROM Table2 WHERE score >= 135)
```
> | ID | name | height | weight |
> | ---------- | ----------- | ---------- | ----------- | 
> | 3 | Mark | 183 | 90 |
> | 4 | Rose | 163 | 45 |
> | 5 | Tom | 172 | 70 |

Back to [Contents](#Contents)
<br>

## CASE
The `CASE` statement goes through conditions and returns a value when the first condition is met (like an IF-THEN-ELSE statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the `ELSE` clause.  
<br>
**Syntax**  
```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN ...
    ELSE result
END
```
or  
```sql
CASE expression
    WHEN value1 THEN result1
    WHEN value2 THEN result2
    WHEN ...
    ELSE result
END
```
Note : if there is no `ELSE` part and no conditions are true, it returns NULL.

【Example】   
There is an existing table called "MyTable" :   
| ID | degree | 
| ---------- | ----------- | 
| 01 | A | 
| 02 | D | 
| 03 | C | 
| 04 | B | 
| 05 | A | 

```sql
SELECT ID, CASE 
    WHEN degree='A' THEN 100
    WHEN degree='B' THEN 80
    WHEN degree='C' THEN 60
    ELSE 40
END
AS degree
FROM MyTable
# or 
# SELECT ID, CASE degree
#     WHEN 'A' THEN 100
#     WHEN 'B' THEN 80
#     WHEN 'C' THEN 60
#     ELSE 40
# END
# FROM MyTable
```
> | ID | degree | 
> | ---------- | ----------- | 
> | 01 | 100 | 
> | 02 | 40 | 
> | 03 | 60 | 
> | 04 | 80 | 
> | 05 | 100 | 

Back to [Contents](#Contents)
<br>
