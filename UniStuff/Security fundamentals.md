# The Triad CIA
![[TRIO.png|100%]]
## Confidentiality
Protecting information from disclosure to unauthorized parties
## Integrity
Protecting information from being modified by unauthorized parties
## Availability
Ensuring that information is available to authorized parties
# Identity and AAA
## Authorization
Authorization is, abstractly spoken, making a decision if a subject, for example, a person is a member of an authorized party that can access certain data, program, etc
To do this you first need to associate an identity with the subject
## Identification
Identification is associating an identity with a subject
## Authentication
Authentication is the step where the system checks if the identity provided by the system entity is valid 
## Access Control
Controlling access of system entities to objects based on an access control policy
## MFA
MFA combines multiple authentication methods from the same type or different types
types are:
- Something you know
- Something you have
- Something you are
- Context location
# Authentication Methods
## Biometrics
these are fingerprints, retina, face id. The problem with biometric is that if the data is stolen it cannot be changed, and can easily been stolen
# Access Control
Access control might come in various forms
- Physical protection e.g. gates
- network traffic e.g. firewalls
- Hardware e.g. memory management
- Operating System e.g. file system
- Application level e.g. Google login, databases
## Access Control Models
typical access control models focus on authorization
- Specification on who is allowed to do what
- How to update/change permissions
a simple access control model (AC) is a relation
- AC = Subject * Object * Request
example of a simple permission check
- (Achim, ExamECM2426, set) $\in$ AC
## Policies vs Models
### Policies
A security policy defines what is allowed or forbidden
- It is analogous to a set of laws
- Defined in terms of rules and/or requirements
### Models
A security model is a representation of a class of systems
- Highlights security features on a chosen level of abstraction
- Provides a vocabulary to develop specific policies
## Access Control Matrix Model
This model is based on the ideas of privileges of subjects on objects (kinda like linux file perms if you think about it)
- Subjects: users, processes, agents, groups, ...
- Objects: data, memory banks, other processes, files, ...
- Privileges: right to read, write, modify
It does this in the context of matrices like the following
![[acmatrix.png|100%]]
### Issues
Not scale-able as it needs to be made for each user and decided who can access what
# Role Based Access Control
Role based access control is built upon the idea that subjects often have roles and roles share the same rights, so RBAC will create roles for jobs and then assign the users to roles and give them a set of permissions to each role (Like AD)