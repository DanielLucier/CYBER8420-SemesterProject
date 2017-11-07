Using Microsoft Threat Modeling Tool 2016 (TMT 2016), Cyber Wardens developed Level 1 data flow diagrams (DFD) to support each of our <a href="https://github.com/DanielLucier/CYBER8420-SemesterProject/tree/master/MisuseCases">misuse cases</a>. We analyzed the DFDs to identify applicable STRIDE threats. We examined each threat automatically identified by TMT 2016 and documented mitigation strategies. A full HTML report was generated using TMT 2016. Finally, we reviewed Keycloak's actual software design for security related issues based on our threat models.

Identify Mitigation Strategies
------------------------------

<strong>Third Party Applications to/from Keycloak</strong>: 1 - 11, 40 - 42 -- Person responsible: Kero
<br /><strong>End User to/from Keycloak</strong>: 12 - 22, 37 - 39 -- Person Responsible: Dan
<br /><strong>LDAP/Active Directory to/from Keycloak</strong>: 23 - 36 -- Person Responsible: Chet
<br /><strong>Client Adapters to/from Keycloak</strong>: 43 - 53, 71 - 73 -- Person Responsible: ??
<br /><strong>Database to/from Keycloak</strong>: 54 - 70 -- Person Responsible: Glenn

Summary Of Security Related Issues Identified In Keycloak's Software Design
----------------------------------------------------------------------------
