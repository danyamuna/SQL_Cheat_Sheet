## SQL JOIN
A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

### Different Types of SQL JOINs
Here are the different types of the JOINs in SQL:

**(INNER) JOIN**
Returns records that have matching values in both tables

**LEFT (OUTER) JOIN**
Returns all records from the left table, and the matched records from the right table.

**RIGHT (OUTER) JOIN**
Returns all records from the right table, and the matched records from the left table

**FULL (OUTER) JOIN** 
Returns all records when there is a match in either left or right table


## SQL INNER JOIN

The SQL INNER JOIN joins two tables based on a common column, and selects records that have matching values in these columns.


Example
```md
SELECT Customers.customer_id, Customers.first_name, Orders.amount
FROM Customers
INNER JOIN Orders
ON Customers.customer_id = Orders.customer;
```

Here, the SQL command selects customer_id and first_name columns 

(from the Customers table) and the amount column (from the Orders table).

And, the result set will contain those rows where there is a match between customer_id 

(of the Customers table) and customer (of the Orders table).

Syntax of INNER JOIN
The syntax of INNER JOIN is:
```md
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
INNER JOIN With WHERE Clause
```

Here's an example of the INNER JOIN with the WHERE clause:
```md
SELECT Customers.customer_id, Customers.first_name, Orders.amount
FROM Customers
INNER JOIN Orders
ON Customers.customer_id = Orders.customer
WHERE Orders.amount >= 500;
```

## Left (Outer) Join

## SQL LEFT JOIN Keyword
The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.
```md
LEFT JOIN Syntax
SELECT column_name(s)
FROM table1
LEFT JOIN table2
```

ON table1.column_name = table2.column_name;

Note: In some databases LEFT JOIN is called LEFT OUTER JOIN.

The SQL LEFT JOIN joins two tables based on a common column, 

and selects records that have matching values in these columns and remaining rows from the left table.

# Example
```md
SELECT Customers.customer_id, Customers.first_name, Orders.amount
FROM Customers
LEFT JOIN Orders
ON Customers.customer_id = Orders.customer;

```

### Right (Outer) Join

SQL RIGHT JOIN Keyword

The RIGHT JOIN keyword returns all records from the right table (table2), 

and the matching records from the left table (table1). 

The result is 0 records from the left side, if there is no match.
```md
RIGHT JOIN Syntax
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```
> Note: In some databases RIGHT JOIN is called RIGHT OUTER JOIN.


## SQL FULL OUTER JOIN Keyword
The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.

Tip: FULL OUTER JOIN and FULL JOIN are the same.
```md
FULL OUTER JOIN Syntax
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

> Note: FULL OUTER JOIN can potentially return very large result-sets!


