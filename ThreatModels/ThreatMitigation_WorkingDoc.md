Interaction: Authentication Request -- Third Party Application to Keycloak
--------------------------------------------------------------------------

1. Spoofing the Third Party Application External Entity  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Third Party Application may be spoofed by an attacker and this may lead to unauthorized access to Keycloak. Consider using a standard authentication mechanism to identify the external entity.
<br />Justification:	<strong>no mitigation provided</strong>
  
2. Elevation Using Impersonation  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Keycloak may be able to impersonate the context of Third Party Application in order to gain additional privilege.
<br />Justification:	<strong>no mitigation provided</strong>
  
3. Cross Site Request Forgery  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Cross-site request forgery (CSRF or XSRF) is a type of attack in which an attacker forces a user's browser to make a forged request to a vulnerable site by exploiting an existing trust relationship between the browser and the vulnerable web site. In a simple scenario, a user is logged in to web site A using a cookie as a credential. The other browses to web site B. Web site B returns a page with a hidden form that posts to web site A. Since the browser will carry the user's cookie to web site A, web site B now can take any action on web site A, for example, adding an admin to an account. The attack can be used to exploit any requests that the browser automatically authenticates, e.g. by session cookie, integrated authentication, IP whitelisting, … The attack can be carried out in many ways such as by luring the victim to a site under control of the attacker, getting the user to click a link in a phishing email, or hacking a reputable web site that the victim will visit. The issue can only be resolved on the server side by requiring that all authenticated state-changing requests include an additional piece of secret payload (canary or CSRF token) which is known only to the legitimate web site and the browser and which is protected in transit through SSL/TLS. See the Forgery Protection property on the flow stencil for a list of mitigations.
<br />Justification:	<strong>no mitigation provided</strong>
  
4. Elevation by Changing the Execution Flow in Keycloak  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	An attacker may pass data into Keycloak in order to change the flow of program execution within Keycloak to the attacker's choosing.
<br />Justification:	<strong>no mitigation provided</strong>
  
5. Keycloak May be Subject to Elevation of Privilege Using Remote Code Execution  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Third Party Application may be able to remotely execute code for Keycloak.
<br />Justification:	<strong>no mitigation provided</strong>
  
6. Data Flow Authentication Request Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
7. Potential Process Crash or Stop for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	Keycloak crashes, halts, stops or runs slowly; in all cases violating an availability metric.
<br />Justification:	<strong>no mitigation provided</strong>
  
8. Data Flow Sniffing  [State: Not Started]  [Priority: High]  
Category:	Information Disclosure
Description:	Data flowing across Authentication Request may be sniffed by an attacker. Depending on what type of data an attacker can read, it may be used to attack other parts of the system or simply be a disclosure of information leading to compliance violations. Consider encrypting the data flow.
<br />Justification:	<strong>no mitigation provided</strong>
  
9. Potential Data Repudiation by Keycloak  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	Keycloak claims that it did not receive data from a source outside the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
10. Potential Lack of Input Validation for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Tampering
Description:	Data flowing across Authentication Request may be tampered with by an attacker. This may lead to a denial of service attack against Keycloak or an elevation of privilege attack against Keycloak or an information disclosure by Keycloak. Failure to verify that input is as expected is a root cause of a very large number of exploitable issues. Consider all paths and the way they handle data. Verify that all input is verified for correctness using an approved list input validation approach.
<br />Justification:	<strong>no mitigation provided</strong>
  
11. Spoofing the Keycloak Process  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Keycloak may be spoofed by an attacker and this may lead to information disclosure by Third Party Application. Consider using a standard authentication mechanism to identify the destination process.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: Authentication Request -- End User to Keycloak
-----------------------------------------------------------

12. Spoofing the End User External Entity  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	End User may be spoofed by an attacker and this may lead to unauthorized access to Keycloak. Consider using a standard authentication mechanism to identify the external entity.
<br />Justification:	<strong>no mitigation provided</strong>
  
13. Elevation Using Impersonation  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Keycloak may be able to impersonate the context of End User in order to gain additional privilege.
<br />Justification:	<strong>no mitigation provided</strong>
  
14. Cross Site Request Forgery  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Cross-site request forgery (CSRF or XSRF) is a type of attack in which an attacker forces a user's browser to make a forged request to a vulnerable site by exploiting an existing trust relationship between the browser and the vulnerable web site. In a simple scenario, a user is logged in to web site A using a cookie as a credential. The other browses to web site B. Web site B returns a page with a hidden form that posts to web site A. Since the browser will carry the user's cookie to web site A, web site B now can take any action on web site A, for example, adding an admin to an account. The attack can be used to exploit any requests that the browser automatically authenticates, e.g. by session cookie, integrated authentication, IP whitelisting, … The attack can be carried out in many ways such as by luring the victim to a site under control of the attacker, getting the user to click a link in a phishing email, or hacking a reputable web site that the victim will visit. The issue can only be resolved on the server side by requiring that all authenticated state-changing requests include an additional piece of secret payload (canary or CSRF token) which is known only to the legitimate web site and the browser and which is protected in transit through SSL/TLS. See the Forgery Protection property on the flow stencil for a list of mitigations.
<br />Justification:	<strong>no mitigation provided</strong>
  
15. Elevation by Changing the Execution Flow in Keycloak  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	An attacker may pass data into Keycloak in order to change the flow of program execution within Keycloak to the attacker's choosing.
<br />Justification:	<strong>no mitigation provided</strong>
  
16. Keycloak May be Subject to Elevation of Privilege Using Remote Code Execution  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	End User may be able to remotely execute code for Keycloak.
<br />Justification:	<strong>no mitigation provided</strong>
  
17. Data Flow Authentication Request Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
18. Potential Process Crash or Stop for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	Keycloak crashes, halts, stops or runs slowly; in all cases violating an availability metric.
<br />Justification:	<strong>no mitigation provided</strong>
  
19. Data Flow Sniffing  [State: Not Started]  [Priority: High]  
Category:	Information Disclosure
Description:	Data flowing across Authentication Request may be sniffed by an attacker. Depending on what type of data an attacker can read, it may be used to attack other parts of the system or simply be a disclosure of information leading to compliance violations. Consider encrypting the data flow.
<br />Justification:	<strong>no mitigation provided</strong>
  
20. Potential Data Repudiation by Keycloak  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	Keycloak claims that it did not receive data from a source outside the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
21. Potential Lack of Input Validation for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Tampering
Description:	Data flowing across Authentication Request may be tampered with by an attacker. This may lead to a denial of service attack against Keycloak or an elevation of privilege attack against Keycloak or an information disclosure by Keycloak. Failure to verify that input is as expected is a root cause of a very large number of exploitable issues. Consider all paths and the way they handle data. Verify that all input is verified for correctness using an approved list input validation approach.
<br />Justification:	<strong>no mitigation provided</strong>
  
22. Spoofing the Keycloak Process  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Keycloak may be spoofed by an attacker and this may lead to information disclosure by End User. Consider using a standard authentication mechanism to identify the destination process.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: Authentication Request -- LDAP/Active Directory to Keycloak
------------------------------------------------------------------------

23. Data Flow Authentication Request Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
24. External Entity LDAP/Active Directory Potentially Denies Receiving Data  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	LDAP/Active Directory claims that it did not receive data from a process on the other side of the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
25. Spoofing of the LDAP/Active Directory External Destination Entity  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	LDAP/Active Directory may be spoofed by an attacker and this may lead to data being sent to the attacker's target instead of LDAP/Active Directory. Consider using a standard authentication mechanism to identify the external entity.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: Authentication Response -- LDAP/Active Directory to Keycloak
-------------------------------------------------------------------------

26. Spoofing the LDAP/Active Directory External Entity  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	LDAP/Active Directory may be spoofed by an attacker and this may lead to unauthorized access to Keycloak. Consider using a standard authentication mechanism to identify the external entity.
<br />Justification:	<strong>no mitigation provided</strong>
  
27. Elevation Using Impersonation  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Keycloak may be able to impersonate the context of LDAP/Active Directory in order to gain additional privilege.
<br />Justification:	<strong>no mitigation provided</strong>
  
28. Cross Site Request Forgery  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Cross-site request forgery (CSRF or XSRF) is a type of attack in which an attacker forces a user's browser to make a forged request to a vulnerable site by exploiting an existing trust relationship between the browser and the vulnerable web site. In a simple scenario, a user is logged in to web site A using a cookie as a credential. The other browses to web site B. Web site B returns a page with a hidden form that posts to web site A. Since the browser will carry the user's cookie to web site A, web site B now can take any action on web site A, for example, adding an admin to an account. The attack can be used to exploit any requests that the browser automatically authenticates, e.g. by session cookie, integrated authentication, IP whitelisting, … The attack can be carried out in many ways such as by luring the victim to a site under control of the attacker, getting the user to click a link in a phishing email, or hacking a reputable web site that the victim will visit. The issue can only be resolved on the server side by requiring that all authenticated state-changing requests include an additional piece of secret payload (canary or CSRF token) which is known only to the legitimate web site and the browser and which is protected in transit through SSL/TLS. See the Forgery Protection property on the flow stencil for a list of mitigations.
<br />Justification:	<strong>no mitigation provided</strong>
  
29. Elevation by Changing the Execution Flow in Keycloak  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	An attacker may pass data into Keycloak in order to change the flow of program execution within Keycloak to the attacker's choosing.
<br />Justification:	<strong>no mitigation provided</strong>
  
30. Keycloak May be Subject to Elevation of Privilege Using Remote Code Execution  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	LDAP/Active Directory may be able to remotely execute code for Keycloak.
<br />Justification:	<strong>no mitigation provided</strong>
  
31. Data Flow Authentication Response Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
32. Potential Process Crash or Stop for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	Keycloak crashes, halts, stops or runs slowly; in all cases violating an availability metric.
<br />Justification:	<strong>no mitigation provided</strong>
  
33. Data Flow Sniffing  [State: Not Started]  [Priority: High]  
Category:	Information Disclosure
Description:	Data flowing across Authentication Response may be sniffed by an attacker. Depending on what type of data an attacker can read, it may be used to attack other parts of the system or simply be a disclosure of information leading to compliance violations. Consider encrypting the data flow.
<br />Justification:	<strong>no mitigation provided</strong>
  
34. Potential Data Repudiation by Keycloak  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	Keycloak claims that it did not receive data from a source outside the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
35. Potential Lack of Input Validation for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Tampering
Description:	Data flowing across Authentication Response may be tampered with by an attacker. This may lead to a denial of service attack against Keycloak or an elevation of privilege attack against Keycloak or an information disclosure by Keycloak. Failure to verify that input is as expected is a root cause of a very large number of exploitable issues. Consider all paths and the way they handle data. Verify that all input is verified for correctness using an approved list input validation approach.
<br />Justification:	<strong>no mitigation provided</strong>
  
36. Spoofing the Keycloak Process  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Keycloak may be spoofed by an attacker and this may lead to information disclosure by LDAP/Active Directory. Consider using a standard authentication mechanism to identify the destination process.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: Authentication Response -- End User to Keycloak
------------------------------------------------------------

37. Data Flow Authentication Response Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
38. External Entity End User Potentially Denies Receiving Data  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	End User claims that it did not receive data from a process on the other side of the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
39. Spoofing of the End User External Destination Entity  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	End User may be spoofed by an attacker and this may lead to data being sent to the attacker's target instead of End User. Consider using a standard authentication mechanism to identify the external entity.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: Authentication Response -- Third Party Application to Keycloak
---------------------------------------------------------------------------

40. Data Flow Authentication Response Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
41. External Entity Third Party Application Potentially Denies Receiving Data  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	Third Party Application claims that it did not receive data from a process on the other side of the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
42. Spoofing of the Third Party Application External Destination Entity  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Third Party Application may be spoofed by an attacker and this may lead to data being sent to the attacker's target instead of Third Party Application. Consider using a standard authentication mechanism to identify the external entity.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: Client Registration -- Client Adapters to Keycloak
---------------------------------------------------------------

43. Elevation Using Impersonation  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Keycloak may be able to impersonate the context of Client Adapters in order to gain additional privilege.
<br />Justification:	<strong>no mitigation provided</strong>
  
44. Spoofing the Client Adapters External Entity  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Client Adapters may be spoofed by an attacker and this may lead to unauthorized access to Keycloak. Consider using a standard authentication mechanism to identify the external entity.
<br />Justification:	<strong>no mitigation provided</strong>
  
45. Spoofing the Keycloak Process  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Keycloak may be spoofed by an attacker and this may lead to information disclosure by Client Adapters. Consider using a standard authentication mechanism to identify the destination process.
<br />Justification:	<strong>no mitigation provided</strong>
  
46. Potential Lack of Input Validation for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Tampering
Description:	Data flowing across Client Registration may be tampered with by an attacker. This may lead to a denial of service attack against Keycloak or an elevation of privilege attack against Keycloak or an information disclosure by Keycloak. Failure to verify that input is as expected is a root cause of a very large number of exploitable issues. Consider all paths and the way they handle data. Verify that all input is verified for correctness using an approved list input validation approach.
<br />Justification:	<strong>no mitigation provided</strong>
  
47. Potential Data Repudiation by Keycloak  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	Keycloak claims that it did not receive data from a source outside the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
48. Data Flow Sniffing  [State: Not Started]  [Priority: High]  
Category:	Information Disclosure
Description:	Data flowing across Client Registration may be sniffed by an attacker. Depending on what type of data an attacker can read, it may be used to attack other parts of the system or simply be a disclosure of information leading to compliance violations. Consider encrypting the data flow.
<br />Justification:	<strong>no mitigation provided</strong>
  
49. Potential Process Crash or Stop for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	Keycloak crashes, halts, stops or runs slowly; in all cases violating an availability metric.
<br />Justification:	<strong>no mitigation provided</strong>
  
50. Data Flow Client Registration Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
51. Keycloak May be Subject to Elevation of Privilege Using Remote Code Execution  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Client Adapters may be able to remotely execute code for Keycloak.
<br />Justification:	<strong>no mitigation provided</strong>
  
52. Elevation by Changing the Execution Flow in Keycloak  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	An attacker may pass data into Keycloak in order to change the flow of program execution within Keycloak to the attacker's choosing.
<br />Justification:	<strong>no mitigation provided</strong>
  
53. Cross Site Request Forgery  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Cross-site request forgery (CSRF or XSRF) is a type of attack in which an attacker forces a user's browser to make a forged request to a vulnerable site by exploiting an existing trust relationship between the browser and the vulnerable web site. In a simple scenario, a user is logged in to web site A using a cookie as a credential. The other browses to web site B. Web site B returns a page with a hidden form that posts to web site A. Since the browser will carry the user's cookie to web site A, web site B now can take any action on web site A, for example, adding an admin to an account. The attack can be used to exploit any requests that the browser automatically authenticates, e.g. by session cookie, integrated authentication, IP whitelisting, … The attack can be carried out in many ways such as by luring the victim to a site under control of the attacker, getting the user to click a link in a phishing email, or hacking a reputable web site that the victim will visit. The issue can only be resolved on the server side by requiring that all authenticated state-changing requests include an additional piece of secret payload (canary or CSRF token) which is known only to the legitimate web site and the browser and which is protected in transit through SSL/TLS. See the Forgery Protection property on the flow stencil for a list of mitigations.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: JDBC Query -- Database to Keycloak
------------------------------------------------

54. Spoofing of Destination Data Store Database  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Database may be spoofed by an attacker and this may lead to data being written to the attacker's target instead of Database. Consider using a standard authentication mechanism to identify the destination data store.
<br />Justification:	<strong>no mitigation provided</strong>
  
55. Potential Excessive Resource Consumption for Keycloak or Database  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	Does Keycloak or Database take explicit steps to control resource consumption? Resource consumption attacks can be hard to deal with, and there are times that it makes sense to let the OS do the job. Be careful that your resource requests don't deadlock, and that they do timeout.
<br />Justification:	<strong>no mitigation provided</strong>
  
56. Spoofing the Keycloak Process  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Keycloak may be spoofed by an attacker and this may lead to unauthorized access to Database. Consider using a standard authentication mechanism to identify the source process.
<br />Justification:	<strong>no mitigation provided</strong>
  
57. The Database Data Store Could Be Corrupted  [State: Not Started]  [Priority: High]  
Category:	Tampering
Description:	Data flowing across JDBC Query may be tampered with by an attacker. This may lead to corruption of Database. Ensure the integrity of the data flow to the data store.
<br />Justification:	<strong>no mitigation provided</strong>
  
58. Data Store Denies Database Potentially Writing Data  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	Database claims that it did not write data received from an entity on the other side of the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
59. Data Flow Sniffing  [State: Not Started]  [Priority: High]  
Category:	Information Disclosure
Description:	Data flowing across JDBC Query may be sniffed by an attacker. Depending on what type of data an attacker can read, it may be used to attack other parts of the system or simply be a disclosure of information leading to compliance violations. Consider encrypting the data flow.
<br />Justification:	<strong>no mitigation provided</strong>
  
60. Data Flow JDBC Query Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
61. Data Store Inaccessible  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent prevents access to a data store on the other side of the trust boundary.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: Result Set -- Database to Keycloak
------------------------------------------------

62. Spoofing of Source Data Store Database  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Database may be spoofed by an attacker and this may lead to incorrect data delivered to Keycloak. Consider using a standard authentication mechanism to identify the source data store.
<br />Justification:	<strong>no mitigation provided</strong>
  
63. Weak Access Control for a Resource  [State: Not Started]  [Priority: High]  
Category:	Information Disclosure
Description:	Improper data protection of Database can allow an attacker to read information not intended for disclosure. Review authorization settings.
<br />Justification:	<strong>no mitigation provided</strong>
  
64. Spoofing the Keycloak Process  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Keycloak may be spoofed by an attacker and this may lead to information disclosure by Database. Consider using a standard authentication mechanism to identify the destination process.
<br />Justification:	<strong>no mitigation provided</strong>
  
65. Potential Data Repudiation by Keycloak  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	Keycloak claims that it did not receive data from a source outside the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
66. Potential Process Crash or Stop for Keycloak  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	Keycloak crashes, halts, stops or runs slowly; in all cases violating an availability metric.
<br />Justification:	<strong>no mitigation provided</strong>
  
67. Data Flow Result Set Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>
  
68. Data Store Inaccessible  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent prevents access to a data store on the other side of the trust boundary.
<br />Justification:	<strong>no mitigation provided</strong>
  
69. Keycloak May be Subject to Elevation of Privilege Using Remote Code Execution  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	Database may be able to remotely execute code for Keycloak.
<br />Justification:	<strong>no mitigation provided</strong>
  
70. Elevation by Changing the Execution Flow in Keycloak  [State: Not Started]  [Priority: High]  
Category:	Elevation Of Privilege
Description:	An attacker may pass data into Keycloak in order to change the flow of program execution within Keycloak to the attacker's choosing.
<br />Justification:	<strong>no mitigation provided</strong>

Interaction: Token Registration -- Client Adapters to Keycloak
--------------------------------------------------------------

71. Spoofing of the Client Adapters External Destination Entity  [State: Not Started]  [Priority: High]  
Category:	Spoofing
Description:	Client Adapters may be spoofed by an attacker and this may lead to data being sent to the attacker's target instead of Client Adapters. Consider using a standard authentication mechanism to identify the external entity.
<br />Justification:	<strong>no mitigation provided</strong>
  
72. External Entity Client Adapters Potentially Denies Receiving Data  [State: Not Started]  [Priority: High]  
Category:	Repudiation
Description:	Client Adapters claims that it did not receive data from a process on the other side of the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
<br />Justification:	<strong>no mitigation provided</strong>
  
73. Data Flow Token Registration Is Potentially Interrupted  [State: Not Started]  [Priority: High]  
Category:	Denial Of Service
Description:	An external agent interrupts data flowing across a trust boundary in either direction.
<br />Justification:	<strong>no mitigation provided</strong>

