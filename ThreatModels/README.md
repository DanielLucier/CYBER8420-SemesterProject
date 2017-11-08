Using Microsoft Threat Modeling Tool 2016 (TMT 2016), Cyber Wardens developed Level 1 data flow diagrams (DFD) to support each of our <a href="https://github.com/DanielLucier/CYBER8420-SemesterProject/tree/master/MisuseCases">misuse cases</a>. We analyzed the DFDs to identify applicable STRIDE threats. We examined each threat automatically identified by TMT 2016 and documented mitigation strategies. A full HTML report was generated using TMT 2016. Finally, we reviewed Keycloak's actual software design for security related issues based on our threat models.

Identify Mitigation Strategies
------------------------------

<a href = "https://daniellucier.github.io/CYBER8420-SemesterProject/ThreatModels/Reports/Keycloak-Threat-Report.html">Click here to view the Keycloak Threat Report in HTML format</a>

<a href = "https://daniellucier.github.io/CYBER8420-SemesterProject/ThreatModels/Reports/Keycloak-Threat-Report.pdf">Click here to view the Keycloak Threat Report in PDF format</a>

Summary Of Security Related Issues Identified In Keycloak's Software Design
----------------------------------------------------------------------------

Using the Microsoft threat Modeling Tool we developed a level 1 data flow diagram. Further reserch found some possible vulnerabilities along with documented <a href = "https://www.cvedetails.com/vulnerability-list/vendor_id-16498/Keycloak.html">CVE's</a>.

Keycloak is a single process that has incoming and outgoing data traffic on multiple fronts (i.e.: an end user, third party applications, LDAP/Active Directory, client adapters, and a data source). Since Keycloak cannot ensure the security of each of these external interactors, a single trust boundary has been placed around the Keycloak process to fully protect the main process.

A main concern that the TMT bought up is the Authentication Request/Response. Three of the five interactors that were determined brought the Elevation of Privilege and Spoofing threats to the forefront. To mitigate an Elevation of Privilege attack on Keycloak, it was determined that all input and output be scrubbed for any code that would negatively affect either process. To mitigate the threat of Spoofing, the traffic between Keycloak and the external interactor must be secured using SSL and encrypted.

The Keycloak community have openly worked on securing the data flow between the process and the interactor. During the work effort of <a href = "https://issues.jboss.org/browse/KEYCLOAK-687?_sscc=t"> documenting security vulnerabilities and solutions </a> the community showed that SSL/HTTPS mode mitigates spoofing attempts. 


https://www.cvedetails.com/vulnerability-list/vendor_id-16498/Keycloak.html

https://issues.jboss.org/browse/KEYCLOAK-687?_sscc=t

https://issues.jboss.org/projects/KEYCLOAK/issues/KEYCLOAK-5459?filter=allopenissues






