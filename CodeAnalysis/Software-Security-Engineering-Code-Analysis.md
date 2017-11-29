**Cyber 8420 Software Security Engineering Code Analysis**
=============================================================

**Open Source Project:** Keycloak

**Authors:** Glenn Anderson, Dan Lucier, Chet Cyr, Kerolos Lotfy

**Team Name:** Cyber Wardens

**Code Review Strategy**

Cyber Wardens decided to use two automated code scanning tools, SonarQube and FindBugs, as well as researching existing CVEs for Keycloak to point us in the right direction to complete manual code review as well.  

**Automated Code Scanning**

&emsp;Sonar is a static code analysis tool that provides a suite of tools to review a developer’s code. For the analysis of Keycloak I used the free open source tool SonarQube. Using java’s building technology Maven, I was able to add a new goal to analysis and publish the code analysis online at <a href = "https://sonarcloud.io/dashboard?id=org.keycloak%3Akeycloak-parent"> SonarQube Projects</a>. Sonar rates the code in four main areas: Bugs/Vulnerabilities, Code Smells, Coverage, and Duplications. Although not everything that Sonar finds is an actual issue, the results are not promising. Although the code passed the overall grade, the Bugs, Vulnerabilities, coverage and duplications all retrieved an E grade.

<br>&emsp;Sonar found 347 bugs and 591 vulnerabilities. While diving into the issues found, Sonar provides the exact locations of each of the issues along with the reason and how to resolve the issue. The issues range from making values into a static variable to not using values that are returned from functions. Code Smell refers to symptoms in the code that might indicate deeper architectural problems. This includes technical debt referring to how much effort it will take to correct the underlining issues. Keycloak has 306 days of technical debt but due to the 476k lines of code still retrieved an A grade. Sonar was also able to find 11k lines of code that were attempts to cover the architectural issues. While diving into the issues, many of the issues were parameters being passed into functions were never used. Sonar’s coverage refers to the amount of code that is flex and tested using various types of unit tests. With 255 different unit tests only a fraction of the Keycloak software is protected or tested. When diving into the tests that are integrated it appears that many of the tests cover the security aspects such as parsing and input validation. Lastly duplications refers to the amount of code that is similar or just plainly copied from place to place for ease of use. Of the 476k lines of code Sonar found that 2,831 blocks of code have been duplicated. Although the official score is 55% duplicated, this is due to the included libraries of angular. The library is stored in multiple places making some files 100% duplicated which is misleading. 

<br>&emsp;Sonar provides some great resources to determine the state of a developer’s code. The four main sections are just a fraction of the information that is provided. There are even sections for reliability, security and maintainability. However for the Keycloak community to be able to address these issues more tests need to be written to provide assurance that any fixes won’t break existing functionality. 

**Manual Code Review**

<br> The team continued with the static code analysis by searching for any known vulnerabilities for Keycloak through the 'National Vulnerability Database'. There were 5 noted vulnerabilities that are associated with Keycloak. Cyber Wardens started with analyzing the noted vulnerabilities and following through the issue tracking and verifying they were patched. 

<br> The highest rated vulnerability is 'CVE-2017-7474' which is found in Keyloack Node.js adapter 2.5 - 3.0. In which tokens were not handled properly. This vulnerability would affect the three pillars of the CIA triad (Confidentiality, Integrity, and availability). The issue was reported by Chess Hazlett in which he noted that the auth-utils grant manager in node.js causes token validity to be ignored during validateGrant(). On 2017-05-08 15:21:20 EDT the issue was addressed by the team and the solution stated the following: 

"The References section of this erratum contains a download link (you must log in to download the update).  Remove your existing Node.js adapter directory and unzip the update file into its place. Then change the dependency for keycloak-connect in the package.json of your application: change dependency file name to keycloak-connect-2.5.5-Final-redhat-3.tgz." Reference Link: (https://access.redhat.com/errata/RHSA-2017:1203)
Rated: 9.8 Critical

<br> The second highest rated vulnerability is 'CVE-2014-3709' which effects the org.keycloak.services.resources.SocialResource.callback method in JBoss on all versions before 1.0.3 final. This vulnerability leverages the lack of CSRF protection to conduct cross-site request forgery attacks (CSRF). This would affect the three pillars of the CIA triad (Confidentiality, Integrity, and availability). This vulnerability was mitigated by the red hat community that supports Keycloak in version 1.0.3 or higher.
Rated: 8.8 High

Redhat community bug tracking: (https://bugzilla.redhat.com/show_bug.cgi?id=1154971)

<br> The third highest rated vulnerability is 'CVE-2017-12159' which discovered that the session cookie that is utilized to prevent CSRF is not unique for each session. This would enable an attacker to gain access to an authenticated user session, which would affect the confidentiality pillar of the CIA triad. 

rated: 7.5 High

<br> The team noted that most of the vulnerabilities were tracked through red hat, which has a very strong community presence. Patches were generally deployed within a week or so of discovery.

