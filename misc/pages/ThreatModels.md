---
layout: default
title: 8420 Threat Models
description: CYBR 8420 Threat Models
---
Threat Models
=============
&emsp;Using Microsoft Threat Modeling Tool 2016 (TMT 2016), Cyber Wardens developed Level 1 data flow diagrams (DFD) to support each of our <a href="https://daniellucier.github.io/CYBER8420-SemesterProject/misc/pages/MisuseCases.html"><strong>misuse cases</strong></a>. We analyzed the DFDs to identify applicable STRIDE threats. We examined each threat automatically identified by TMT 2016 and documented mitigation strategies. A full HTML report was generated using TMT 2016. Finally, we reviewed Keycloak's actual software design for security related issues based on our threat models.

Identify Mitigation Strategies
------------------------------

<a href = "https://daniellucier.github.io/CYBER8420-SemesterProject/ThreatModels/TMT2016Docs/Keycloak-Threat-Model.htm"><strong>Click here to view the Keycloak Threat Report</strong></a>

Summary of Security Related Issues Identified in Keycloak's Software Design
----------------------------------------------------------------------------

&emsp;Keycloak is a single process that has incoming and outgoing data traffic on multiple fronts (i.e.: an end user, third party applications, LDAP/Active Directory, client adapters, and a data source). Since Keycloak cannot ensure the security of each of these external interactors, a single trust boundary has been placed around the Keycloak process to fully protect the main process.

&emsp;A main concern that the TMT bought up is the Authentication Request/Response. Three of the five interactors that were determined brought the Elevation of Privilege and Spoofing threats to the forefront. To mitigate an Elevation of Privilege attack on Keycloak, it was determined that all input and output be scrubbed for any code that would negatively affect either process. To mitigate the threat of Spoofing, the traffic between Keycloak and the external interactor must be secured, using SSL, and encrypted.

&emsp;The Keycloak community have openly worked on securing the data flow between the process and the external interactor. During the work effort of <a href = "https://issues.jboss.org/browse/KEYCLOAK-687?_sscc=t"><strong>documenting security vulnerabilities and solutions</strong></a>, the community showed that SSL/HTTPS mode mitigates spoofing attempts. Further research found some possible vulnerabilities along with documented <a href = "https://www.cvedetails.com/vulnerability-list/vendor_id-16498/Keycloak.html"><strong>CVE's</strong></a>. 

&emsp;<a href="http://www.keycloak.org/docs/3.3/server_admin/topics/threat.html"><strong>Section 3.19, Threat Model Mitigation,</strong></a> of Keycloak's documentation discusses possible security vulnerabilities that could be encountered by any authentication server and provides mitigation strategies to address the vulnerabilities. According to <a href = "http://www.keycloak.org/docs/3.3/server_admin/topics/threat/csrf.html"><strong>the CSRF section</strong></a>, a possible CSRF vulnerability is identified, and a mitigation strategy is provided:

<span style="padding-left: 20px; display:block">"The only part of Keycloak that really falls into CSRF is the user account management pages. To mitigate this Keycloak sets a state cookie and also embeds the value of this state cookie within hidden form fields or query parameters in action links. This query or form parameter is checked against the state cookie to verify that the call was made by the user."</span>





