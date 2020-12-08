# SQL Programming Notes

## Contents
* [Create the Empty Table](#Create_the_Empty_Table)
* [SELECT](#SELECT)
* [SELECT DISTINCT](#SELECT_DISTINCT)
* [INSERT INTO](#INSERT_INTO) 
* [UPDATE](#UPDATE)
* [WHERE](#WHERE)
* [ORDER BY](#ORDER_BY)
* [GROUP BY](#GROUP_BY)

## Create_the_Empty_Table  
**Syntax**
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
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
<br>  
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






