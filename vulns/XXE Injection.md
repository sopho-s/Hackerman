# XML
XML is a markup language derived from SGML which is used by HTML. XML is typically used by applications to store and transport data in a format that's both human-readable and machine parseable
## Syntax and structure
```xml
<?xml version="1.0" encoding="UTF-8"?>
<user id="1">
   <name>John</name>
   <age>30</age>
   <address>
      <street>123 Main St</street>
      <city>Anytown</city>
   </address>
</user>
```
XML elements are represented by tags, which are surrounded by angle brackets that usually come in pairs
## XSLT
XSLT is a language used to transform and format XML documents. While primarily used for data transformation and formatting, it is also significantly relevant to XXE attacks
## DTD
DTDs define the structure and constraints of an XML document. They specify the allowed elements, attributes, and relationships between them
DTDs can be used to declare external entities like external files or urls (idk why i said like they are literally the only two options)
## ENTITTIES (spooky)
Entities are placeholders for data or code that can be expanded within an XML document
### Types of entities
#### Internal entities
Internal entities are variables used within an XML document to define and substitute content that may be repeated multiple times
par example
```xml
<!DOCTYPE note [
<!ENTITY inf "This is a test.">
]>
<note>
        <info>&inf;</info>
</note>
```
#### External entities
Similar to internal entities, but their contents are referenced from outside the XML document, such as from a separate file or url
```xml
<!DOCTYPE note [
<!ENTITY ext SYSTEM "http://example.com/external.dtd">
]>
<note>
        <info>&ext;</info>
</note>
```
#### Parameter entities
Parameter entities are a special type of entity used to define a reusable structures or to include external DTD subsets
```xml
<!DOCTYPE note [
<!ENTITY % common "CDATA">
<!ELEMENT name (%common;)>
]>
<note>
        <name>John Doe</name>
</note>
```
In this example %common is used within the DTD to define the type of data that the name element should contain
#### General entities
General entities are similar to variables and can be declared wither internally or externally. They are used to define substitutions that can be used within the body of the XML document
#### Character entities
Character entities are used to represent special or reserved characters that cannot be used directly in xml documents
```xml
<note>
        <text>Use &lt; to represent a less-than symbol.</text>
</note>
```
## In Band XXE
In band XXE refers to an XXE vulnerability where the attacker can see the response from the server. this allows for straightforward data exfiltration and exploitation
You can abuse this by trying to include internal or external files using internal and external entities respectively
## Out of band XXE
Out of band XXE refers to when the attacker cannot directly see the response from the server, but from another location such as their own http server
## SSRF + XXE
Using XXE vulnerabilities one can use the server to request internal or otherwise privilege requiring requests through the servers permissions
# Mitigation
- Disable external entities and DTDs
- Use less complex data formats like JSON
- Allowlisting input validation