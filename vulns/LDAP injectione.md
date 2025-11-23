LDAP is a protocol used for accessing and maintaining distributed directory information services over a network. In LDAP, directory entries are structured as objects, they follow a hierarchical structure like a file system's tree
at the top is the TLD underneath there may be subdomains or organisational units
- Distinguished names (DNs): serve as unique identifiers for each entry in the directory, specifying the path from the top of the LDAP tree to the entry
- Relative distinguished names: represents an individuals levels within the hierarchy
- Attributes: define the properties of directory entries
# Search queries
LDAP search queries are used to interact is LDAP directories. An LDAP search query consists of several components, each serving a specific function in the search operation
- Base DN: This is the search's starting point in the directory tree
- Scope: Defines how deep the search should go from the base DN. It can be one of the following:
	- base (search the base DN only)
	- one (search the immediate children of the base DN)
	- sub (search the base DN and all its descendants)
- Filter: A criteria entry must match to be returned in the search results. It uses a specific syntax to define these criteria
- Attributes: Specifies which characteristics of the matching entries should be returned in the search results
the basic syntax for an LDAP search query looks like this:
```
(base DN) (scope) (filter) (attributes)
```
Filters also allow you to use wildcard and logical operators
# Bypass techs 
## Tautology-based injection
this type of injection involves inserting conditions into an LDAP query that are inherently true, thus ensuring the query always returns a positive result
here is an example where `*)(|(&` is passed for `{userInput}` and `pwd)` for `{passwordInput}`
```
(&(uid=*)(|(&)(userPassword=pwd)))
```
this always will return try therefore return the first user in the LDAP datastructure
## Wildcard injection
Wildcards are used in LDAP queries to match any sequence of characters, making them easy to bypass authentication
## Blind
While there is no specific way, like with SQL where you could use sleeps, one can look at the resulting output of the webpage to gauge the result of the query