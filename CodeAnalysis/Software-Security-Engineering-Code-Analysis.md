**Cyber 8420 Software Security Engineering Code Analysis**
=============================================================

**Open Source Project:** Keycloak

**Authors:** Glenn Anderson, Dan Lucier, Chet Cyr, Kerolos Lotfy

**Team Name:** Cyber Wardens

<br> The team started the code analysis by searching for any known vulnerabilities for Keycloak through the 'National Vulnerability Database'. There were 5 noted vulnerabilities that are associated with Keycloak. Cyber Wardens' started with analyzing the noted vulnerabilities and following through the issue tracking and verifying they were patched. 

<br> The highest rated vulnerability is 'CVE-2017-7474' which is found in Keyloack Node.js adapter 2.5 - 3.0. In which tokens were not handled properly. This vulnerability would affect the three pillars of the CIA triad (Confidentiality, Integrity, and availability). The issue was reported by Chess Hazlett in which he noted that the auth-utils grant manager in node.js causes token validity to be ignored during validateGrant(). On 2017-05-08 15:21:20 EDT the issue was addressed by the team and the solution stated the following: 

"The References section of this erratum contains a download link (you must log in to download the update).  Remove your existing Node.js adapter directory and unzip the update file into its place. Then change the dependency for keycloak-connect in the package.json of your application: change dependency file name to keycloak-connect-2.5.5-Final-redhat-3.tgz." Reference Link: (https://access.redhat.com/errata/RHSA-2017:1203)
Rated: 9.8 Critical

<br> The second highest rated vulnerability is 'CVE-2014-3709' which effects the org.keycloak.services.resources.SocialResource.callback method in JBoss on all versions before 1.0.3 final. This vulnerability leverages the lack of CSRF protection to conduct cross-site request forgery attacks (CSRF). This would affect the three pillars of the CIA triad (Confidentiality, Integrity, and availability). This vulnerability was mitigated by the red hat community that supports Keycloak in version 1.0.3 or higher.
Rated: 8.8 High

Redhat community bug tracking: (https://bugzilla.redhat.com/show_bug.cgi?id=1154971)

<br> The third highest rated vulnerability is 'CVE-2017-12159' which discovered that the session cookie that is utilized to prevent CSRF is not unique for each session. This would enable an attacker to gain access to an authenticated user session, which would affect the confidentiality pillar of the CIA triad. 

rated: 7.5 High

<br> The team noted that most of the vulnerabilities were tracked through red hat, which has a very strong community presence. Patches were generally deployed within a week or so of discovery.

