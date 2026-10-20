# SQL_Cheat_Sheet
## SQL CREATE DATABASE Statement
```md
CREATE DATABASE myDataBase;
IF NOT EXISTS(SELECT * FROM sys.databases WHERE name = 'myDataBase')
  BEGIN
    CREATE DATABASE myDataBase;
END
```

## Switch Databases
```m
We have to work across multiple databases from time to time. To switch between available databases, we can run the following statement.
USE myDataBase;
```

## SQL DROP DATABASE Statement
```md
In SQL, DROP DATABASE is used to delete the database in our Database Management System. For example,

DROP DATABASE myDataBase;

IF EXISTS(SELECT * FROM sys.databases WHERE name = 'koko')
  BEGIN
    Drop DATABASE koko;
END
```
## SQL CREATE TABLE 
```md
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```

## SQL DROP TABLE Statement
```md
In SQL, DROP TABLE is used to delete the tables in our database. For example,

DROP TABLE Employees;
ALTER TABLE Employees // Add Column
ADD Gendor char(1);
ALTER TABLE Employees //Rename a Column
RENAME COLUMN Gendor TO Gender;
ALTER TABLE OldTableName //Rename a Table
RENAME TO NewTableName;
ALTER TABLE Employees //Modify Column in a Table
ALTER COLUMN Name VARCHAR(100);
ALTER TABLE Employees //Delete a column
DROP COLUMN Gender;
```
### Backup & Restore Database
## Backup Database
````md
It is important to create database backups regularly so that our data won't get lost if the database gets corrupted.
In SQL, we can create database backups using the BACKUP DATABASE statement
```sql
BACKUP DATABASE MyDatabase1
TO DISK = 'C:\MyDatabase1_backup.bak';
```
````
## Differential Backup
A differential back up only backs up the parts of the database that have changed since the last full database backup.
In SQL, we can create differential database backups using the BACKUP DATABASE With Differential  statement.
```sql
BACKUP DATABASE MyDatabase1
TO DISK = 'C:\MyDatabase1_backup.bak'
```
## Restore Database From Backup
To restore a backup file to the database management system, we can use the RESTORE DATABASE statement. 
```sql
RESTORE DATABASE MyDatabase1
FROM DISK = 'C:\MyDatabase1.bak'
```
````

