# Constraints
Constraints can be specified when the table is created with the CREATE TABLE statement, 

or after the table is created with the ALTER TABLE statement.

Syntax
```md
CREATE TABLE table_name (
   column1 datatype constraint,
   column2 datatype constraint,
   column3 datatype constraint,
   ....
);
```
# SQL Constraints
SQL constraints are used to specify rules for the data in a table.

Constraints are used to limit the type of data that can go into a table.

This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.

Constraints can be column level or table level. Column level constraints apply to a column, 

and table level constraints apply to the whole table.

The following constraints are commonly used in SQL:

> NOT NULL - Ensures that a column cannot have a NULL value
> 
> UNIQUE - Ensures that all values in a column are different
> 
> PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
> 
> FOREIGN KEY - Prevents actions that would destroy links between tables
> 
> CHECK - Ensures that the values in a column satisfies a specific condition
> 
> DEFAULT - Sets a default value for a column if no value is specified
> 
> CREATE INDEX - Used to create and retrieve data from the database very quickly

# SQL PRIMARY KEY Constraint
The PRIMARY KEY constraint uniquely identifies each record in a table.

Primary keys must contain UNIQUE values, and cannot contain NULL values.

A table can have only ONE primary key; and in the table, this primary key can consist of single or multiple columns (fields).

### SQL PRIMARY KEY on CREATE TABLE
The following SQL creates a PRIMARY KEY on the "ID" column when the "Persons" table is created:
```md
CREATE TABLE Persons (
   ID int NOT NULL PRIMARY KEY,
   LastName varchar(255) NOT NULL,
   FirstName varchar(255),
   Age int
);
```
To allow naming of a PRIMARY KEY constraint, and for defining a PRIMARY KEY constraint on multiple columns,

use the following SQL syntax:
```md
CREATE TABLE Persons (
   ID int NOT NULL,
   LastName varchar(255) NOT NULL,
   FirstName varchar(255),
   Age int,
    CONSTRAINT PK_Person PRIMARY KEY (ID,LastName)
);
```
> Note: In the example above there is only ONE PRIMARY KEY (PK_Person). However, the VALUE of the primary key is made up of TWO COLUMNS (ID + LastName).

### SQL PRIMARY KEY on ALTER TABLE
To create a PRIMARY KEY constraint on the "ID" column when the table is already created, use the following SQL:
```md
ALTER TABLE Persons
ADD PRIMARY KEY (ID);
```

To allow naming of a PRIMARY KEY constraint, and for defining a PRIMARY KEY constraint on multiple columns, use the following SQL syntax:
```md
ALTER TABLE Persons
ADD CONSTRAINT PK_Person PRIMARY KEY (ID,LastName);
```
> Note: If you use ALTER TABLE to add a primary key, the primary key column(s) must have been declared **to not contain NULL values**
(when the table was first created).
```md
DROP a PRIMARY KEY Constraint
To drop a PRIMARY KEY constraint, use the following SQL:
```
```md
ALTER TABLE Persons
DROP CONSTRAINT PK_Person;
```

# SQL FOREIGN KEY Constraint
The FOREIGN KEY constraint is used to prevent actions that would destroy links between tables.

A FOREIGN KEY is a field (or collection of fields) in one table, that refers to the PRIMARY KEY in another table.

SQL FOREIGN KEY on CREATE TABLE

The following SQL creates a FOREIGN KEY on the "PersonID" column when the "Orders" table is created:
```md
CREATE TABLE Orders (
   OrderID int NOT NULL PRIMARY KEY,
   OrderNumber int NOT NULL,
   PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
);
```

To allow naming of a FOREIGN KEY constraint, and for defining a FOREIGN KEY constraint on multiple columns, use the following SQL syntax:

```md
CREATE TABLE Orders (
   OrderID int NOT NULL,
   OrderNumber int NOT NULL,
   PersonID int,
    PRIMARY KEY (OrderID),
    CONSTRAINT FK_PersonOrder FOREIGN KEY (PersonID)
    REFERENCES Persons(PersonID)
);
```
## SQL FOREIGN KEY on ALTER TABLE
To create a FOREIGN KEY constraint on the "PersonID" column when the "Orders" table is already created, use the following SQL:
```md
ALTER TABLE Orders
ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
```
> To allow naming of a FOREIGN KEY constraint, and for defining a FOREIGN KEY constraint on multiple columns, use the following SQL syntax:
```md
ALTER TABLE Orders
ADD CONSTRAINT FK_PersonOrder
FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
```
```md
DROP a FOREIGN KEY Constraint

```
**To drop a FOREIGN KEY constraint, use the following SQL:**
```md
ALTER TABLE Orders
DROP CONSTRAINT FK_PersonOrder;
```

# SQL NOT NULL on CREATE TABLE
The following SQL ensures that the "ID", "LastName", and "FirstName" columns will NOT accept NULL values when the "Persons" table is created:

Example

```md
CREATE TABLE Persons (
   ID int NOT NULL,
    LastName varchar(255) NOT NULL,
   FirstName varchar(255) NOT NULL,
   Age int
);
```

### SQL NOT NULL on ALTER TABLE
To create a NOT NULL constraint on the "Age" column when the "Persons" table is already created, use the following SQL:
```md
ALTER TABLE Persons
ALTER COLUMN Age int NOT NULL;
```

# SQL DEFAULT Constraint

The DEFAULT constraint is used to set a default value for a column.

The default value will be added to all new records, if no other value is specified.

SQL DEFAULT on CREATE TABLE

The following SQL sets a DEFAULT value for the "City" column when the "Persons" table is created:
```md
CREATE TABLE Persons (
   ID int NOT NULL,
   LastName varchar(255) NOT NULL,
   FirstName varchar(255),
   Age int,
   City varchar(255) DEFAULT 'Amman'
);
```
The DEFAULT constraint can also be used to insert system values, by using functions like GETDATE():
```md
CREATE TABLE Orders (
   ID int NOT NULL,
   OrderNumber int NOT NULL,
   OrderDate date DEFAULT GETDATE()
);
```
### SQL DEFAULT on ALTER TABLE
To create a DEFAULT constraint on the "City" column when the table is already created, use the following SQL:
```md
ALTER TABLE Persons
ADD CONSTRAINT df_City
DEFAULT 'Amman' FOR City;
```


**DROP a DEFAULT Constraint**
To drop a DEFAULT constraint, use the following SQL:
```md
ALTER TABLE Persons
DROP Constraint  df_City;
```

 # SQL CHECK Constraint
The CHECK constraint is used to limit the value range that can be placed in a column.

If you define a CHECK constraint on a column it will allow only certain values for this column.

If you define a CHECK constraint on a table it can limit the values in certain columns based on values in other columns in the row.

**SQL CHECK on CREATE TABLE**

The following SQL creates a CHECK constraint on the "Age" column when the "Persons" table is created. 

The CHECK constraint ensures that the age of a person must be 18, or older:
```md
CREATE TABLE Persons (
   ID int NOT NULL,
   LastName varchar(255) NOT NULL,
   FirstName varchar(255),
   Age int CHECK (Age>=18)
);
```

> To allow naming of a CHECK constraint, and for defining a CHECK constraint on multiple columns, use the following SQL syntax:
```md
CREATE TABLE Persons (
   ID int NOT NULL,
   LastName varchar(255) NOT NULL,
   FirstName varchar(255),
   Age int,
   City varchar(255),
    CONSTRAINT CHK_Person CHECK (Age>=18 AND City='Amman')
);
```

**DROP a CHECK Constraint**
To drop a CHECK constraint, use the following SQL:
```md
ALTER TABLE Persons
DROP CONSTRAINT CHK_Person;
```

# SQL UNIQUE Constraint
The UNIQUE constraint ensures that **all values in a column are different**.

> Both the UNIQUE and PRIMARY KEY constraints provide a guarantee for uniqueness for a column or set of columns.

A PRIMARY KEY constraint automatically has a **UNIQUE constraint**.

> However, you can have many UNIQUE constraints per table, but only one PRIMARY KEY constraint per table.

**SQL UNIQUE Constraint on CREATE TABLE**
The following SQL creates a UNIQUE constraint on the "ID" column when the "Persons" table is created:

SQL Server:
```md

CREATE TABLE Persons (
   ID int NOT NULL UNIQUE,
   LastName varchar(255) NOT NULL,
   FirstName varchar(255),
   Age int
);
```

To name a UNIQUE constraint, and to define a UNIQUE constraint on multiple columns, use the following SQL syntax:

CREATE TABLE Persons (
   ID int NOT NULL,
   LastName varchar(255) NOT NULL,
   FirstName varchar(255),
   Age int,
    CONSTRAINT UC_Person UNIQUE (ID,LastName)
);



**SQL UNIQUE Constraint on ALTER TABLE**

To create a UNIQUE constraint on the "ID" column when the table is already created, use the following SQL:

```md
ALTER TABLE Persons
ADD UNIQUE (ID);
```
To name a UNIQUE constraint, and to define a UNIQUE constraint on multiple columns, use the following SQL syntax:
```md

ALTER TABLE Persons
ADD CONSTRAINT UC_Person UNIQUE (ID,LastName);
```
**DROP a UNIQUE Constraint**

To drop a UNIQUE constraint, use the following SQL:

SQL Server :
```md

ALTER TABLE Persons
DROP CONSTRAINT UC_Person;
```
#  SQL Index

**SQL CREATE INDEX Statement**
The CREATE INDEX statement is used to create indexes in tables.

Indexes are used to retrieve data from the database more quickly than otherwise. The users cannot see the indexes, they are just used to speed up searches/queries.

> Note: Updating a table with indexes takes more time than updating a table without (because the indexes also need an update). So, only create indexes on columns that will be frequently searched against.

**CREATE INDEX Syntax**
Creates an index on a table. Duplicate values are allowed:
```md
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```

**CREATE UNIQUE INDEX Syntax**
Creates a unique index on a table. Duplicate values are not allowed:
```md
CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);
```
**CREATE INDEX Example**
The SQL statement below creates an index named "idx_lastname" on the "LastName" column in the "Persons" table:
```md
CREATE INDEX idx_lastname
ON Persons (LastName);
```

> If you want to create an index on a combination of columns, you can list the column names within the parentheses, separated by commas:
```md
CREATE INDEX idx_pname
ON Persons (LastName, FirstName);
```
**DROP INDEX Statement**
The DROP INDEX statement is used to delete an index in a table.
```md
DROP INDEX table_name.index_name;
```


SQL Server Clustered Index and Primary key constraint
When you create a table with a primary key, SQL Server automatically creates a corresponding clustered index that includes primary key columns.



Clustered Index is much faster than normal Index.
