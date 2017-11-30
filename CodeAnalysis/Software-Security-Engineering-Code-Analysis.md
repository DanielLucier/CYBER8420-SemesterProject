**Cyber 8420 Software Security Engineering Code Analysis**
=============================================================

**Open Source Project:** Keycloak

**Authors:** Glenn Anderson, Dan Lucier, Chet Cyr, Kerolos Lotfy

**Team Name:** Cyber Wardens

Code Review Strategy
--------------------
Cyber Wardens decided to use two automated code scanning tools, SonarQube and PMD. The review strategy for manual code analysis was risk based by research existing CVEs for Keycloak to point us in the right direction to complete manual code review.  

Automated Code Scanning
-----------------------
<strong>Tool 1:</strong>

&emsp;Sonar is a static code analysis tool that provides a suite of tools to review a developer’s code. For the analysis of Keycloak I used the free open source tool SonarQube. Using java’s building technology Maven, I was able to add a new goal to analysis and publish the code analysis online at <a href = "https://sonarcloud.io/dashboard?id=org.keycloak%3Akeycloak-parent"> SonarQube Projects</a>. Sonar rates the code in four main areas: Bugs/Vulnerabilities, Code Smells, Coverage, and Duplications. Although not everything that Sonar finds is an actual issue, the results are not promising. Although the code passed the overall grade, the Bugs, Vulnerabilities, coverage and duplications all retrieved an E grade.

&emsp;Sonar found 347 bugs and 591 vulnerabilities. While diving into the issues found, Sonar provides the exact locations of each of the issues along with the reason and how to resolve the issue. The issues range from making values into a static variable to not using values that are returned from functions. Code Smell refers to symptoms in the code that might indicate deeper architectural problems. This includes technical debt referring to how much effort it will take to correct the underlining issues. Keycloak has 306 days of technical debt but due to the 476k lines of code still retrieved an A grade. Sonar was also able to find 11k lines of code that were attempts to cover the architectural issues. While diving into the issues, many of the issues were parameters being passed into functions were never used. Sonar’s coverage refers to the amount of code that is flex and tested using various types of unit tests. With 255 different unit tests only a fraction of the Keycloak software is protected or tested. When diving into the tests that are integrated it appears that many of the tests cover the security aspects such as parsing and input validation. Lastly duplications refers to the amount of code that is similar or just plainly copied from place to place for ease of use. Of the 476k lines of code Sonar found that 2,831 blocks of code have been duplicated. Although the official score is 55% duplicated, this is due to the included libraries of angular. The library is stored in multiple places making some files 100% duplicated which is misleading. 


<strong>Tool 2:</strong>

<strong>Hardware:</strong> Windows 10 Enterprise 2016 LTSB
<br><strong>Java Develpoment Kit:</strong> Java SE 9.0.1
<br><strong>Java Runtime Environment:</strong> Java 8 update 151
<br><strong>Static Code Analysis Tool:</strong> PMD 5.8.1

<br>&emsp;After all listed software was donwloaded, Keycloak (downloaded as .zip from Github) and PMD (downloaded as .zip from PMD website) were extracted to the desktop. All of the .java and .js files from Keycloak were copied into a seperate folder (Keycloak-SourceCode). PMD was run from the command line to analyz the Keycloak files.
<br><br>&emsp;&emsp;C:\Users\student\desktop\pmd-bin-5.8.1\pmd-bin-5.8.1\bin> pmd -d C:\Users\student\desktop\Keycloak-SourceCode 
<br>&emsp;&emsp;-f xml -R rulesets/internal/all-java.xml > C:\Users\student\desktop\pmd-results

<br>&emsp;PMD is an open source static code analyzer that scans source code in multiple languages for possible bugs, dead code, suboptimal code, overcomplicated expressions, and duplicate code. A total of 194,920 violations were identified with 21,961 unique types. “Potential violation of Law of Demeter…” accounted for the largest number of violations. “Method chain calls” accounted for 37,759 violations (overall highest number of violations), “object not created locally” accounted for 19,118, and “static property access” accounted for 1,622. According to PMD’s documentation, the Law of Demeter “is a simple rule, that says ‘only talk to friends’. It helps to reduce coupling between classes or objects.” The Law of Demeter is also known as the principle of least knowledge. These violations could be a good starting point for strengthening the codebase and contributing to the community.

<a href="https://github.com/DanielLucier/CYBER8420-SemesterProject/blob/master/CodeAnalysis/Misc/pmd_results/pmd-results.xlsx">Click here for an excel view of the PMD results.</a>

<a href="https://unomaha.box.com/s/9cfp34t56457u4f2w8sm603f9432w0ad">This link contains the HTML version of PMD's results.</a>

Manual Code Review
------------------
&emsp;The team continued with the static code analysis by searching for any known vulnerabilities for Keycloak through the 'National Vulnerability Database'. There were 5 noted vulnerabilities that are associated with Keycloak. Cyber Wardens started with analyzing the noted vulnerabilities and following through the issue tracking and verifying they were patched. 

&emsp;The highest rated vulnerability is 'CVE-2017-7474' which is found in Keyloack Node.js adapter 2.5 - 3.0. In which tokens were not handled properly. This vulnerability would affect the three pillars of the CIA triad (Confidentiality, Integrity, and availability). The issue was reported by Chess Hazlett in which he noted that the auth-utils grant manager in node.js causes token validity to be ignored during validateGrant(). On 2017-05-08 15:21:20 EDT the issue was addressed by the team and the solution stated the following: 

&emsp;"The References section of this erratum contains a download link (you must log in to download the update).  Remove your existing Node.js adapter directory and unzip the update file into its place. Then change the dependency for keycloak-connect in the package.json of your application: change dependency file name to keycloak-connect-2.5.5-Final-redhat-3.tgz." Reference Link: (https://access.redhat.com/errata/RHSA-2017:1203)

Please Note: the direct file that was effected could be found in the following github pull request to fix the issue: https://github.com/keycloak/keycloak-nodejs-auth-utils/pull/49/files

Rated: 9.8 Critical

The major changes that were made in this pull request included token validation to verify that tokens are valid, missing, signed, etc.

This CVE most closely maps to Cyber Wardens’ misuse case three which is related to minimizing unauthorized access.

&emsp;The second highest rated vulnerability is 'CVE-2014-3709' which effects the org.keycloak.services.resources.SocialResource.callback method in JBoss. This vulnerability leverages the lack of CSRF protection to conduct cross-site request forgery attacks (CSRF). This would affect the three pillars of the CIA triad (Confidentiality, Integrity, and availability). This vulnerability was mitigated by the red hat community that supports Keycloak in version 1.0.3 or higher.

&emsp;This vulnerability fix was can be viewed on the source code at https://github.com/keycloak/keycloak/blob/4b254475dad05741ab8ec88243dfbd35f7674aa4/services/src/main/java/org/keycloak/services/resources/SocialResource.java#L104 This fix was to validate and sanitize any incoming date from the call back function. This was obvious when viewing the threat model that we created. 


Rated: 8.8 High

Redhat community bug tracking: (https://bugzilla.redhat.com/show_bug.cgi?id=1154971)


Summary of Key Findings
-----------------------
&emsp;The Keycloak community provides a few outlets for its bug tracking and vulnerabilities, including a JIRA bug tracking and Github tracking. However, looking though, the finding of Sonar and PMD that were quite a few findings that are still open and should be corrected. Both tools found parameters orphaned in functions, and Sonar specifically found massive amounts of code that are not protected through testing.  I believe that by adding unit tests issues that the automated tools found can be fixed by anyone with a sense of assurance. 

&emsp;The community is heading in the right direction. With the CVE-2017-7474 for using an invalid token fix, the user took it upon themselves to add a test to ensure that this type of vulnerability would not be exploited again. Amount the critical issue found in the CVE, Sonar found 218 blockers that given more time would be a great location to start.

