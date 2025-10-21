Repeater allows for capturing, modifying, and resending the same request multiple times. This functionality is particularly useful when crafting payloads through trial and error
# Sending groups
Using the repeater one can send multiple requests at once using groups and then sending the group
## Sending group in sequence
sending a group in sequence provides two options
- Send group in sequence (**single connection**)
- Send group in sequence (**separate connections**)
### Single connection
This option establishes a single connection to the server and sends all the requests in the group's tabs before closing the connection. this can be useful for testing for potential client-side desync vulnerabilities
### Seperate connections
This option establishes a TCP connection for each request
## Sending group in parallel
Choosing to send the group's requests in parallel would trigger the repeater to send all the requests in the group at once