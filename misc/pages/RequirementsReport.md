---
layout: default
title: 8420 Requirements Report
description: CYBR 8420 Requirements Report
---
Assurance Claims
----------------
Below is a list of the five top level assurance claims developed by Cyber Wardens:
<ol type="1">
  <li>User credentials are transmitted to third party applications over secure channels.</li>
  <li>Stored user credentials are protected from unauthorized access.</li>
  <li>Sanitizing the input values from adding a new user minimizes the possibility of maliciously affecting Keycloak.</li>
  <li>Keycloak minimizes non-administrative users access to the server admin console.</li>
  <li>Keycloak is protected against brute force attacks.</li>
</ol>

Security Requirements
---------------------
After developing assurance cases for each top level assurance claim, Cyber Wardens developed misuse cases to address the claims. A diagram for each misuse case was developed in Lucidchart. <a href="https://www.lucidchart.com/invitations/accept/8f828c56-45d6-4af2-81cc-23e43b10af5a">Click here to view our misuse case diagrams.</a> From these misuse cases, several security requirements were identified:

<ul>
  <li>The communication that is sent over the network/internet is encrypted.</li>
  <li>SSL encryption is supported.</li>
  <li>Passwords are stored in the application as ciphertext.</li>
  <li>A salt is added to passwords prior to encryption.</li>
  <li>The salt is a random combination of ASCII characters.</li>
  <li>A post-quantum cryptography algorithm is used to encrypt passwords.</li>
  <li>Restrict non-admin users from accessing administrator tools.</li>
  <li>Sanitize all user input.</li>
  <li>Set and enforce password complexity policies.</li>
  <li>Set and enforce account lockout parameters.</li>
</ul>

Keycloak Documentation Review
-----------------------------
<a href="http://www.keycloak.org/documentation.html">Click here for Keycloak's documentation.</a>

An important aspect of all applications that can transmit data between client and server is the encryption of the data. To this end, SSL certification on the hosted Keycloak website is essential. To mitigate the possibility of user’s access tokens from being stolen due to a packet sniffer, Keycloak offers three modes for SSL/HTTPS. The SSL mode defines the requirements for interacting with Keycloak. The three modes are: external requests, none, and all. External requests require users to obtain a static IP address (such as IP addresses on the network) to access the Keycloak console. None mode turns off the SSL requirements which could open the network traffic to vulnerabilities. Lastly, all mode requires SSL for all IP addresses, whether internal or external.

Keycloak is a server to client application that adds authentication to applications by storing user's credentials on a company's server. Since user credentials are stored, it is imperative to protect the stored data from unauthorized access. This is accomplished by encrypting stored passwords. In Keycloak documentation 3.6.1, it is noted that passwords are not stored in clear text. Passwords are encrypted before being stored or validated. Keycloak provides PBKDF2 as the only built-in and default encryption algorithm. However, section 5, Server Development, provides instructions on how the user can add a different encryption algorithm. Section 3.6.1 also indicates that, by default, a password is hashed 20,000 times before being stored or validated. According to section 3.6.2, time based and counter based one-time passwords can be generated. Each OTP algorithm uses SHA1 by default. Although the documentation does not explicitly mention salted passwords, a deep dive into the code base, <a href="https://github.com/keycloak/keycloak/blob/a89dbabc921d841dc943ac3a33886396bb13781b/server-spi/src/main/java/org/keycloak/credential/hash/Pbkdf2PasswordHashProvider.java">click here for an example</a>, illustrates that a salt is added to passwords.

“The principle of separation of privilege states that a system should not grant permission based upon a single condition <a href="https://www.us-cert.gov/bsi/articles/knowledge/principles/separation-of-privilege">(Gegick & Barnum, 2005)</a>.” In robust applications, a basic user shouldn’t have the ability to perform administrative actions. In many instances, a user must also possess the correct security permissions to access the administrative tools. Keycloak does this by having one initial admin account and breaking every other user into Roles and Groups. By placing users into corresponding roles/groups, they are given extra security permissions. This allows for the admin to easily and swiftly revoke permissions to users that attempt to misuse the application. Furthering the ability to sign into Keycloak, Active Directory/LDAP are supported allowing for more control over which users on the network can gain access to Keycloak.

With all applications that are exposed to the outside world, password guessing is an important issue. If an attacker can guess the admins password they can essentially bring down the entire company. This could be done by bringing down the servers, installing ransomware, or even reading private emails and attempting to black mail the company’s CEO. To prevent this, software should be able to enforce minimum password requirements and max login failures. Keycloak is no exception to these guidelines. Keycloak allows for admins to enforce a password policy on its users. Some of the policies include: digits, lower case, uppercase, special chars, and a regex pattern. On top of password policies, Keycloak offers the ability to configure the max login failures. After a certain amount of failures, the user will need to wait until after a configurable amount of time before attempting again. 

Configuration and Installation Documentation Review
-----------------------------
An operating mode must first be selected.  There are three operating modes, Standalone, Standalone Clustered, and Domain Clustered.  It is not recommended to run Keycloak in a production environment in stand alone mode due to this being a single point of failure.  The reason that you should choose domain clustered mode over stand-alone clustered mode is because domain clustered mode offers a centralized repository of server configurations within a cluster.  In stand-alone clustered mode each configuration must be updated separately on each server.  This could cause a security risk if the configuration files become out of sync between different clustered servers.  It is also a security risk to run in standalone mode only becuase if the Keycloak server fails, then the end users will not be able to login.  This also means that an attacker would only need to take down one Keycloak server to prevent all users' access.  Ensuring that an administrator chooses the correct operating mode is important when performing initial setup. 

Section 2.6 recommends that an administrator setup a separate relational database than the H2 database that comes with the application because it does not support clustered servers or high activity uses.  Keycloak states that the H2 database that initially comes with it is just so the server can run out of the box.  The documentation then proceeds to explain how to use a separate relational database and integrate it with the system.  This may not be know by some users that are deploying Keycloak.  It is important to know that the out of the box H2 database can fail under higher loads and is not the recommended solution.

Controlling access to the administrative console is required to prevent disgruntled employees or other users from attempting to login and make changes to the passoword policies.  Keycloak accomplishes this by estabilshing separate administration realms that allow different passoword policies to be defined.  The master realm is the default realm that is created when the server is installed.  This is not a recommened area to store password policies.  Only additional realms and administrative accounts should be created within the master realm.  The realms have built in management roles that can be used to define what different administrators can do within the system.  There are also fine grain controls that can be used to create more complex administrative user functions.  Access to these realms is controlled by realm keys that are asymmetric key pairs made up of a private and public key.  Section 3.12 discusses how the realm keys work in greater detail as well as how to handle possible compromised key pairs.

As noted previously Keycloak uses SSL/HTTPS to encrypt the traffic.  However, Keycloak is not setup by default to handle SSL/HTTPS. It either needs to be enabled through the Keycloak server itself or through a reverse proxy that is configured to force traffic through the Keycloak server. Keycloak SSL/HTTPS can be configured based on three different modes.  By default, in the first mode, Keycloack can be run without SSL as long as only private IP addresses are utilized. Therefore, if an external request occurs it would error out since it only accepts connection from private IP addresses. To setup SSL/HTTPS for the Keycloak server it would involve: 
<ul>
   <li> Generating a keystore that would contain the private key along with the certificate for SSL/HTTP traffic. </li>
   <li> Configuring the Keycloak server to utilize the set certificate and keypair.</li>
</ul>

The main goal of utilizing Keycloak is to authenticate through multiple platforms using single-sign on. One of the major security risks is if the password is compromsided. If a hacker can guess the password using a simple brute-force attack then it would be gameover for an oranization. Therefore, one of the security features that should be enabled is the bruteforce detection which is noted in the documentation under section 3.19 'Threat Model Mitigation'. This feature, allows password lockouts and quick login protection (protects against bruteforcing scripts) which would also generate alerts to the adminstrators. Also proper password complexity polices should be setup through the Keyclaok Administration console, these policies help mitigate the potential risk of password bruteforce attacks. When creating these password policies, industry standards should also be followed to prevent bruteforce attacks. 
