## INSERT INTO Statement
```md
The INSERT INTO statement is used to insert new records in a table.

INSERT INTO Syntax
It is possible to write the INSERT INTO statement in two ways:

1. Specify both the column names and the values to be inserted:

INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

2. If you are adding values for all the columns of the table, you do not need to specify the column names in the SQL query. However, make sure the order of the values is in the same order as the columns in the table. Here, the INSERT INTO syntax would be as follows:

INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

##  Update Statement
```md
UPDATE Statement
The UPDATE statement is used to modify the existing records in a table.

UPDATE Syntax
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

Note: Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement.
The WHERE clause specifies which record(s) that should be updated.
If you omit the WHERE clause, all records in the table will be updated!
```

## Delete Statement
```md
DELETE Statement
The DELETE statement is used to delete existing records in a table.

DELETE Syntax
DELETE FROM table_name WHERE condition;

Note: Be careful when deleting records in a table! Notice the WHERE clause in the DELETE statement. The WHERE clause specifies which record(s) should be deleted.
If you omit the WHERE clause, all records in the table will be deleted!
```
## SELECT INTO Statement
```md
In SQL, we can copy data from one database table to a new table using the SELECT INTO command. For example,

SELECT *
INTO EmpoyeesCopy
FROM Employees;
Here, the SQL command copies all data from the Employees table to the new EmployeesCopy table.

Note: The SELECT INTO statement creates a new table. If the database already has a table with the same name, SELECT INTO gives an error.

If we want to copy data to an existing table (rather than creating a new table), we should use the INSERT INTO SELECT statement.
```
## INSERT INTO SELECT Statement
```md
We'll learn to copy records from one table to another with the help of examples.

The INSERT INTO SELECT statement is used to copy records from one table to another existing table. For example,

INSERT INTO OldPersons
SELECT *
FROM Persons;
Run Code

Here, the SQL command copies all records from the Persons table to the OldPersons table.

Note: To run this command,

the database must already have a table named OldPersons
the column names of the OldPersons table and the Persons table must match
If we want to copy data to a new table (rather than copying in an existing table), we should use the SELECT INTO statement.

Copy all columns from one table to another table:

INSERT INTO table2
SELECT * FROM table1
WHERE condition;

Copy only some columns from one table into another table:

INSERT INTO table2 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;
```
