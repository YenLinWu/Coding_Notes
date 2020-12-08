# SQL Programming Notes

## Contents
* [String](#String)
* [List](#List)
* [Dictionary](#Dictionary)
* [Others](#Others)

## Create the Empty Table 
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
Example : 
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


## Create the Table Using Another Table   
A copy of an existing table can be created using `CREATE TABLE`.
```sql
CREATE TABLE new_table_name AS
    SELECT column1, column2,...
    FROM existing_table_name
    WHERE ....;
```
【Example】  
There is a table called 'OrderList' : 
| ID | class | price | quantity |
| ---------- | ----------- | ---------- | ----------- | 
| 1 | A | 500 | 20 |
| 2 | B | 350 | 10 |
| 3 | C | 400 | 15 |
| 4 | A | 200 | 30 |

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




