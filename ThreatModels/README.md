Using Microsoft Threat Modeling Tool 2016 (TMT 2016), Cyber Wardens developed Level 1 data flow diagrams (DFD) to support each of our <a href="https://github.com/DanielLucier/CYBER8420-SemesterProject/tree/master/MisuseCases">misuse cases</a>. We analyzed the DFDs to identify applicable STRIDE threats. We examined each threat automatically identified by TMT 2016 and documented mitigation strategies. A full HTML report was generated using TMT 2016. Finally, we reviewed Keycloak's actual software design for security related issues based on our threat models.

Identify Mitigation Strategies
------------------------------

<a href = "https://daniellucier.github.io/CYBER8420-SemesterProject/ThreatModels/Keycloak-Threat-Report.html">Click here to view the Keycloak Threat Report</a>

Summary Of Security Related Issues Identified In Keycloak's Software Design
----------------------------------------------------------------------------

Using the Microsoft threat Modeling Tool we developed a level 1 data flow diagram and found a some possible vulnerabilities along with documented CVE's.

Keycloak is a single processes that has incoming and outgoing data traffic on multiple fronts including: an end user, third party applications, LDAP/Active Directory, client adapters, and a data source. Since Keycloak cannot ensure the security of each of these external interactor’s a single trust boundary has been placed around the Keycloak process to fully protect the main process.


https://www.cvedetails.com/vulnerability-list/vendor_id-16498/Keycloak.html

https://issues.jboss.org/browse/KEYCLOAK-687?_sscc=t

https://issues.jboss.org/projects/KEYCLOAK/issues/KEYCLOAK-5459?filter=allopenissues






