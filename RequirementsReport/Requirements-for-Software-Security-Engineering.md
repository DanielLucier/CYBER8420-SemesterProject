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
<br />.&emsp;. The communication is encrypted supports modern cryptology along with SSL.
<br />. Passwords are stored in the application as ciphertext.
<br />. A salt is added to passwords prior to encryption.
<br />&emsp;. The salt is a random combination of ASCII characters.
<br />. A post-quantum cryptography algorithm is used to encrypt passwords.
<br />. MisUse3--placeholder
<br />. MisUse4--placeholder

Keycloak Documentation Review
-----------------------------

