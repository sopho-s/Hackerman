IDOR stands for Insecure Direct Object Reference, this type of vuln can occur when a web server recieves user-supplied input to retrieve objects, too much trust has been placed in teh input data, and it is not validated on the server-side
# Encoded IDs
when passing data web devs will usually encode the raw data, encoding makes sure that the web server will be able to understand the contents. decoding the data and manipulating it before re-encoding it may allow you to bypass auth
# Hashed ids
Hashed ids are more complicated than encoded ones, but the hashes can be cracked if you can predict what the data structure might be, you can also use rainbow tables to crack the hash aswell
# Unpredictable ids
If the above two methods dont work you may try making two accounts and switching the ids to check if an IDOR is available#
# Where are these vulns located
the vulnerable endpoint may not always be something you see in the address bar, but may be data loaded in via an AJAX request
