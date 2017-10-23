**Cyber 8420 Requirements for Software Security Engineering**
=============================================================

**Open Source Project:** Keycloak

**Authors:** Glenn Anderson, Dan Lucier, Chet Cyr, Kerolos Lotfy

**Team Name:** Cyber Wardens


Assurance Claims
----------------
Below is a list of five top level assurance claims developed by Cyber Wardens:

1. User credentials are transmitted to third party applications over secure channels.
2. Stored user credentials are protected from unauthorized access.
3. Sanitizing the input values from adding a new user minimizes the possibility of maliciously affecting Keycloak.
4. Keycloak minimizes non-administrative users access to the server admin console.
5. Keycloak is protected against brute force attacks.

Security Requirements
---------------------
After developing assurance cases for each assurance claim, Cyber Wardens developed misuse cases to address the claims. A diagram for each misuse case was developed in Lucidchart. <a href="https://www.lucidchart.com/invitations/accept/8f828c56-45d6-4af2-81cc-23e43b10af5a">Click here to view our misuse case diagrams.</a> From these misuse cases, several security requirements were identified:

<br />. The communication that is sent over the network/internet can be encrypted.
<br />&emsp;. The communication is encrypted supports modern cryptology along with SSL.
<br />. Passwords are stored in the application as ciphertext.
<br />. A salt is added to passwords prior to encryption.
<br />&emsp;. The salt is a random combination of ASCII characters.
<br />. A post-quantum cryptography algorithm is used to encrypt passwords.
<br />. Restricting non admin users from accessesing administrative tools
<br />. Keycloak provides the ability to enforce password complexity and lockout parameters.

Keycloak Documentation Review
-----------------------------

An important aspect of all applications that can transmit data between client and server is the encryption of the data. To this end using a SSL certification on the hosted keycloak website is essential. To mitigate the possibility of user’s access tokens from being stolen due to a packet sniffer, Keycloak offers three modes for SSL/HTTPS. The SSL mode defines the requirements for interacting with Keycloak. The Three modes are: external requests, none, and all. External requests require users to obtain a static IP address (such as IP addresses on the network) to access the Keycloak console. None mode turns off the SSL requirements which would open the network traffic to vulnerabilities. Lastly the mode all requires SSL for all IP addresses, whether internal or external.

Place holder for 2

Separation of Privilege is defined as “The principle of separation of privilege states that a system should not grant permission based upon a single condition”. In robust applications, a basic user shouldn’t have the ability to perform administrative actions. In many instances, a user must also be possessing the correct security permissions to access the administrative tools. Keycloak does this by having one initial admin account, and breaking every other user into a Roles and Groups. By placing users into corresponding roles/groups, they are given extra security permissions. This allows for the admin to easily and swiftly revoke permissions to users that attempt to misuse the application. Furthering the ability to sign into Keycloak, Active Directory/LDAP are supported allowing for more control over which users on the network can gain access to Keycloak.

With all applications that are exposed to the outside world, password guessing is an important issue. If an attacker can guess the admins password they can essentially bring down the entire company. This could be done by bringing down the servers, installing ransomware, or even reading private emails and attempting to black mail the company’s CEO. To prevent this software should be able to enforce minimum password requirements and max login failures. Keycloak is no exception to these guidelines. Keycloak allows for admins to enforce a password policy on its users. Some of the policies include: digits, lower case, uppercase, special chars, and for a regex pattern. On top of password policies, Keycloak offers the ability to configure the max login failures. After a certain amount of failures, the user will need to wait after a configurable amount of time before attempting again. 

Security Related Configuration and Installation
-----------------------------