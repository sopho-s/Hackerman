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