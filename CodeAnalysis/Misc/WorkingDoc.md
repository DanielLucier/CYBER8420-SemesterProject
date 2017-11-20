Project Requirements
=====================
Code analysis for Software Security Engineering: 2-3 page report that describes the following:
* Code review strategy (examples in slides) -- Risk Based
* Manual code review of critical security functions identified in mis-use cases and threat models.
* Automated code scanning (if available). Include links to full reports.
* Summary of key findings from manual and/or automated scanning. This may include: Categorization, Mappings to CWEs, CAPECs, Risk Levels etc.
* Links to any pull requests, issues, discussion, etc. from the team to the original project and any follow-up interactions.

Proposed Work
=====================
Glenn
<br>Sonar is a static code analysis tool. They have an IDE plugin called SonarLint to do analysis on a page your working on, and a free open source full code analysis. Glenn will attempt to run the full code analysis on keycloak pending license issues. because the free sonar publishes the results online, and requires the product to be open source, and have a copy of the source code under the github users account. Ill have to email Gandhi if this breaks the keycloaks Apache License
If this is not a valid option i will chose a few locations in the code and use SonarLint to find issues and manually create a report.

Dan
<br>Another static code reviewing tool, as Gandhi said, one tool isnt always enough. So someone can using tool that was brought up previously in class "Fingbugs, PMD, OWASP"

Chet & Kero
<br>Since KeyCloak had a CVE back in may, i think a static code review on the fixes that were put in place would be a great idea. This would involve looking through the keycloak commits and bug tracking to find references to the CVE and manually looking at the commit. This will include looking at the entire area of change from the beginning of time to current base. this can provide a reasoning why the bug was implemented.
the CVE can be found at https://nvd.nist.gov/vuln/search/results?adv_search=false&form_type=basic&results_type=overview&search_type=all&query=keycloak 

Result
===================
The four options above will cover the strategry (manual and automatic), manual code reviews, and automated code scanning.
Each option will result in maximum two paragraphs on the findings. for the manual code reviews include informaiton such as why the change was made and possible risk levels of the change
As of right now we do not have any pull requests or issues, so this section may be empty unless anything is found.
