# Relational vs non-relational
## Relational database
stores structured data, meaning the data inserted into this database follows a structure. This structured data is stored in rows and columns in a table. Relationships can then be made between two or more tables
## Non-relational databases
unlike relational databases, data is stored in a non-tabular format, this means that the data can be of various quantities and types
## Which to choose
Relational databases are often used when data being stored is reliably going to be received in a consistent format, where accuracy is important
# Creating a database
the following command will create a database with the name specified
```sql
CREATE DATABASE database_name;
```
the following command can then be used to show the created databases along with any other databases
```sql
SHOW DATABASES;
```
the following command then makes it so you use the selected database
```sql
USE databse_name;
```
once the database is no longer needed you can then remove it with the following database
```sql
DROP database database_name;
```
# Creating a table
you can use the following command to create a table
```sql
CREATE TABLE table_name (
	column1_name data_type modifiers,
	column2_name data_type modifiers,
	column3_name data_type modifiers
);
```
you can then use the following command
```sql
SHOW TABLES;
```
If you wish to have a reminder what a table consists of you can use the following command
```sql
DESCRIBE table_name
```
If you wish to change certain parts of the table you can use the following command
```sql
ALTER TABLE table_name
ADD column data_type modifiers;
```
Then if you need to remove the table you can do this
```sql
DROP TABLE table_name;
```
# Modifiers
## AUTO_INCREMENT
this automatically increments the value in this field from the previously added one
## PRIMARY KEY
this makes this column a unique identifier for the row
## NOT NULL
this makes it so that this value may not be empty
# CRUD
crud stands for create, read, update, and delete
## INSERT
```sql
INSERT INTO table_name (column1_name, column2_name)
VALUES (value1, value2);
```
## SELECT
the following command selects all fields from the table
```sql
SELECT * FROM table_name;
```
the following command selects only certain fields from the table
```sql
SELECT field1, field2 FROM table_name
```