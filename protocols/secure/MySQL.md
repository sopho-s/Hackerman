stores data (You know what sql is i dont need to explain)
# Details
- default port is 3306
- uses tcp
# Enumeration
## MSF auxiliary/scanner/mysql/mysql_version
gets the version of the mysql server
## MSF auxiliary/scanner/msql/mysql_login
does a brute force login
## MSF auxiliary/scanner/mysql/mysql_enum
finds a bunch of info about the sql server
## MSF auxiliary/admin/mysql/mysql_sql
allows you to send sql commands to the server
## MSF auxiliary/scanner/mysql/mysql_schemadump