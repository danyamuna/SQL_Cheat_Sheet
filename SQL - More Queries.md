 ## Views

SQL CREATE VIEW Statement

In SQL, a view is a virtual table based on the result-set of an SQL statement.

A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database.

You can add SQL statements and functions to a view and present the data as if the data were coming from one single table.

A view is created with the CREATE VIEW statement. 
```md
CREATE VIEW Syntax
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
> Note: A view always shows up-to-date data! The database engine recreates the view, every time a user queries it

EXISTS Operator
The EXISTS operator is used to test for the existence of any record in a subquery.

The EXISTS operator returns TRUE if the subquery returns one or more records.

## EXISTS Syntax
```md
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```

> The SQL EXISTS operator executes the outer SQL query if the subquery is not NULL (empty result-set).

## UNION Operator
The UNION operator is used to combine the result-set of two or more SELECT statements.

Every SELECT statement within UNION must have the same number of columns

The columns must also have similar data types

The columns in every SELECT statement must also be in the same order

UNION Syntax
```md
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```
UNION ALL Syntax
> The UNION operator selects only distinct values by default. To allow duplicate values, use UNION ALL:
```md
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```
> Note: The column names in the result-set are usually equal to the column names in the first SELECT statement.

## CASE 

The CASE expression goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.

If there is no ELSE part and no conditions are true, it returns NULL.

CASE Syntax
```md
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```
