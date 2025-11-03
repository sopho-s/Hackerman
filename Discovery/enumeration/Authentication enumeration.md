# Identifying valid usernames
knowing a valid username lets an attacker focus just on the password, you can figure out usernames in different ways, like observing how the application responds during login or password resets
# Password policies
The guidelines when creating passwords can provide valuable insights into the complexity of the passwords used in an application. By understanding these policies, an attacker can gauge the potential complexity of the passwords and tailor their strategy accordingly
# Basic Authentication
Basic authentication offers a more straightforward method when securing access to devices. It requires only a username and password
# Common enumeration places
## Registration pages
Web applications typically make the user registration process straight forward and informative by immediately indicating whether an email or username is available. while this feedback is designed to enhance the user experience, we can use it to find the existence of users and add to a list of active users
## Password reset features
Password reset mechanisms are designed to help users regain access to their accounts by entering their details to receive instructions. However the difference in the applications response can unintentionally reveal sensitive info
## Verbose errors
Verbose error messages during login attempts or other interactive processes can reveal too much information, we can use this to identify valid usernames
## Data breach info
Data from previous security breaches is a goldmine for attackers as it allows them to test whether compromised usernames and passwords are reused across different platforms
