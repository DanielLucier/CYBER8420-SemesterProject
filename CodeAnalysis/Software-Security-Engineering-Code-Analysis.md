**Cyber 8420 Software Security Engineering Code Analysis**
=============================================================

**Open Source Project:** Keycloak

**Authors:** Glenn Anderson, Dan Lucier, Chet Cyr, Kerolos Lotfy

**Team Name:** Cyber Wardens

Code Review Strategy
--------------------
&emsp;Cyber Wardens decided to use two automated code scanning tools, SonarQube and PMD.  The analysis for the automated code scanning tools gives highlighted results, but focuses the critical and blocker issues. A risk based review strategy was utilized for manual code analysis. Existing CVEs for Keycloak were researched and guided the manual code review.   

Automated Code Scanning
-----------------------
<strong>Tool 1:</strong>

&emsp;Sonar is a static code analysis tool that provides a suite of tools to review a developer’s code. For the analysis of Keycloak, I used the free open source tool SonarQube. Using java’s building technology Maven, I was able to add a new goal to analysis and publish the code analysis online at <a href = "https://sonarcloud.io/dashboard?id=org.keycloak%3Akeycloak-parent">SonarQube Projects</a>. Sonar rates the code in four main areas: Bugs/Vulnerabilities, Code Smells, Coverage, and Duplications. Although not everything that Sonar finds is an actual issue, the results are not promising. Although the code passed the overall grade, the Bugs/Vulnerabilities, Coverage, and Duplications all retrieved an E rating.

&emsp;Sonar found 347 bugs and 591 vulnerabilities. While diving into the issues found, Sonar provides the exact locations of each of the issues along with the reason and how to resolve the issue. The issues range from making values into a static variable to not using values that are returned from functions. Code Smell refers to symptoms in the code that might indicate deeper architectural problems. This includes technical debt referring to how much effort it will take to correct the underlining issues. Keycloak has 306 days of technical debt, but the large size of the code base still results in an A rating. 

&emsp;Sonar was also able to find 11,000 lines of code that were attempts to cover the architectural issues. Many of these issues are caused by parameters being passed into functions that were never used. Sonar’s Coverage refers to the amount of code that is flex and tested using various types of unit tests. With 255 different unit tests, only a fraction of the Keycloak software is protected or tested. Analyzing the tests, it appears that many covered security aspects such as parsing and input validation. Lastly, Duplications refers to the amount of code that is similar or just copy and pasted. Of the 476,000 lines of code, Sonar found that 2,831 blocks of code that have been duplicated. Although the official duplicated score is 55%, this is due to the included libraries of angular. The library is stored in multiple places making some files 100% duplicated which is a misleading result.

<strong>Tool 2:</strong>

<strong>Hardware:</strong> Windows 10 Enterprise 2016 LTSB
<br><strong>Java Develpoment Kit:</strong> Java SE 9.0.1
<br><strong>Java Runtime Environment:</strong> Java 8 update 151
<br><strong>Static Code Analysis Tool:</strong> PMD 5.8.1

&emsp;After all listed software was downloaded, Keycloak and PMD were extracted to the desktop. All the .java and .js files from Keycloak were copied into a separate folder (Keycloak-SourceCode). PMD was run from the command line to analyze the Keycloak files. 

&emsp;&emsp;C:\Users\student\desktop\pmd-bin-5.8.1\pmd-bin-5.8.1\bin> pmd -d C:\Users\student\desktop\Keycloak-SourceCode 
<br>&emsp;&emsp;-f xml -R rulesets/internal/all-java.xml > C:\Users\student\desktop\pmd-results

&emsp;PMD is an open source static code analyzer that scans source code, in multiple languages, for possible bugs, dead code, suboptimal code, overcomplicated expressions, and duplicate code. A total of 194,920 violations were identified with 21,961 unique types. “Potential violation of Law of Demeter…” accounted for the largest number of violations. “Method chain calls” accounted for 37,759 violations (overall highest number of violations), “object not created locally” accounted for 19,118, and “static property access” accounted for 1,622. According to PMD’s documentation, the Law of Demeter “is a simple rule, that says ‘only talk to friends’. It helps to reduce coupling between classes or objects.” The Law of Demeter is also known as the principle of least knowledge. 

<br><a href="https://github.com/DanielLucier/CYBER8420-SemesterProject/blob/master/CodeAnalysis/Misc/pmd_results/pmd-results.xlsx">Click here for an excel view of the PMD results.</a>
<br><a href="https://unomaha.box.com/s/9cfp34t56457u4f2w8sm603f9432w0ad">This link contains the HTML version of PMD's results.</a>

Manual Code Review
------------------
&emsp;Static code analysis was conducted manually by searching for any known vulnerabilities for Keycloak through the National Vulnerability Database. There were five noted vulnerabilities associated with Keycloak. Analysis began with the noted vulnerabilities, following through the Keycloak issue tracking, and verified the vulnerabilities were patched.

&emsp;The highest rated vulnerability is 'CVE-2017-7474' with a rating of 9.8 (Critical). This vulnerability is found in Keycloak Node.js adapter 2.5 - 3.0 in which tokens were not handled properly. This vulnerability would affect the three CIA pillars (Confidentiality, Integrity, and Availability). The issue was reported by Chess Hazlett. He noted that the auth-utils grant manager in node.js causes token validity to be ignored during validateGrant(). On 2017-05-08 15:21:20 EDT the issue was addressed by the team and the solution stated:

&emsp;"The References section of this erratum contains a download link (you must log in to download the update). Remove your existing Node.js adapter directory and unzip the update file into its place. Then change the dependency for keycloak-connect in the package.json of your application: change dependency file name to keycloak-connect-2.5.5-Final-redhat-3.tgz." Reference Link: (https://access.redhat.com/errata/RHSA-2017:1203)

&emsp;The direct file that was affected could be found in the <a href="https://github.com/keycloak/keycloak-nodejs-auth-utils/pull/49/files"> github pull request</a> to fix the issue. The major changes that were made in this pull request included token validation to verify that tokens are valid, missing, signed, etc.
 
 &emsp;This CVE most closely maps to Cyber Wardens’ misuse case three which is related to minimizing unauthorized access.

&emsp;The second highest rated vulnerability is 'CVE-2014-3709' (rating of 8.8 – High) which affects the org.keycloak.services.resources.SocialResource.callback method in JBoss on all versions before 1.0.3 final. This vulnerability leverages the lack of CSRF protection to conduct cross-site request forgery attacks (CSRF). This would affect the three CIA pillars (Confidentiality, Integrity, and Availability). This vulnerability was mitigated by the Red Hat community that supports Keycloak for version 1.0.3 and later. See<a href="https://bugzilla.redhat.com/show_bug.cgi?id=1154971"> Redhat community bug tracking</a> for more information about this CVE.

&emsp;The fix for this vulnerability can be found at<a href="https://github.com/keycloak/keycloak/blob/4b254475dad05741ab8ec88243dfbd35f7674aa4/services/src/main/java/org/keycloak/services/resources/SocialResource.java#L104"> line 104 of the source code</a>. This fix was to validate and sanitize any incoming data from the callback function. This vulnerability was identified by our Threat Model. 

Summary of Key Findings
-----------------------
&emsp;The Keycloak community provides a few outlets for its bug tracking and vulnerability reporting, including a JIRA bug tracking system and Github tracking. Looking through the findings of Sonar and PMD, there were quite a few findings that are still open and should be corrected. Both tools found parameters orphaned in functions. Sonar specifically found massive amounts of code that are not verified as protected through testing. 

&emsp;Adding unit testing to problem areas identified from the tools, developers have a higher sense of assurance when implementing fixes. With the CVE-2017-7474 for using an invalid token fix, the users took it upon themselves to add a test to ensure that this type of vulnerability would not be exploited again. The 218 blockers identified by Sonar and the Law of Demeter violations identified by PMD could be good starting points for strengthening the codebase and contributing to the community.

