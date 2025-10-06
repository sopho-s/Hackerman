# Logging onto SQL local
```bash
mysql -u root -p
```
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
SELECT field1, field2 FROM table_name;
```
## UPDATE
```sql
UPDATE table_name
SET field = value
WHERE field = value;
```
## DELETE
```sql
DELETE FROM table_name WHERE field = value;
```
# Clauses
clauses are a part of a statement that specifies the criteria of the data being manipulated, this can define the type of data an how it should be retrieved or sorted
## DISTINCT
This clause is used to avoid duplicate records when doing a query, returning only unique values
```sql
SELECT DISTINCT * FROM table_name;
```
## GROUP BY
```sql
SELECT field_name, COUNT(*)
FROM table_name
GROUP BY field_name;
```
## ORDER BY
```sql
SELECT *
FROM table_name
ORDER BY field_name ASC/DESC;
```
## HAVING
```sql
SELECT field_name, COUNT(*)
FROM table_name
GROUP BY field_name
HAVING field_name LIKE '%string%';
```
# Operators
## LIKE
The LIKE operator is commonly used in conjunction with clauses like WHERE in order to filter for specific patterns within a column
```sql
SELECT *
FROM table_name
WHERE field_name LIKE "%string%";
```
## AND
The AND operator uses multiple conditions within a query and returns TRUE if all of them are true
```sql
SELECT *
FROM table_name
WHERE field_name="string" AND field_name="string";
```
## OR
The OR operator uses multiple conditions within a query and returns TRUE if one of them is true
```sql
SELECT *
FROM table_name
WHERE field_name="string" OR field_name="string";
```
## NOT
The NOT operator reverses the value of a boolean operator, allowing us to exclude a specific condition
```sql
SELECT *
FROM table_name
WHERE NOT field_name LIKE "%string%"
```
## BETWEEN
The BETWEEN operator allows us to test if a value exists within a defined range
```sql
SELECT *
FROM table_name
where field_name BETWEEN n_1 and n_2;
```
# Functions
## CONCAT()
this function adds two or more strings together
```sql
SELECT CONCAT(field_name, "string", field_name)
AS new_field_name
FROM table_name;
```
## GROUP_CONCAT()
this function can help us to contatenate data from multiple rows into one field
```sql
SELECT field_name, GROUP_CONCAT(field_name SEPARATOR ", ")
AS new_field_name
FROM table_name
GROUP BY field_name;
```
## SUBSTRING()
this function will retrieve a substring from a string within a query
```sql
SELECT SUBSTRING(field_name, n_1, n_2)
AS new_field_name
FROM table_name;
```
## LENGTH()
This function returns the number of characters in a string
```sql
SELECT LENGTH(field_name)
AS new_field_name
FROM table_name;
```
## SUM()
```sql
SELECT SUM(field_name)
AS new_field_name
FROM table_name;
```
## MAX()
this function calculates the maximum value within a provided column in an expression
```sql
SELECT MAX(field_name)
AS new_field_name
FROM table_name;
```
## MIN()
This function calculates the minimum value within a provided column in an expression
```sql
SELECT MIN(field_name)
AS new_field_name
FROM table_name;
```
