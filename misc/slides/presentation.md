class: center, middle 

  <br><br><br><strong><a href="https://daniellucier.github.io/CYBER8420-SemesterProject">.large[Cyber Wardens]</a></strong>
  <br><br><span style="color:white;">Kero Lotfy, Dan Lucier, Chet Cyr, Glenn Anderson</span>

  
.top-center-logo[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]
.footnote[
\* See notes for logo image source
]
???
Keycloak logo images retrieved from: https://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&uact=8&ved=0ahUKEwjr9JilhPPXAhWr7IMKHU4YBVsQjB0IBg&url=http%3A%2F%2Fwww.keycloak.org%2F&psig=AOvVaw0GUUBPj47YKzf1OEQsXPnc&ust=1512568872641840

---
class: middle

<span style="color:white">
  <strong>Overview</strong>
  <ul>
    <li style="color:white;">Project Description</li>
    <li style="color:white;">Assurance Claims</li>
    <li style="color:white;">Security Requirements</li>
    <li style="color:white;">Code Review</li>
  </ul>
</span>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: center, middle

<span style="color:white">
  <strong>Project Description</strong>
</span>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: middle
  <br>
  <ul>
    <li style="color:white;">Open source identity and access management solution</li>
    <li style="color:white;">Single-Sign On</li>
    <ul "list-style-type: circle">
      <li style="color:white;">Authenticate to Keycloak rather than individual applications</li>
    </ul>
    <li style="color:white;">Provides Kerberos bridge (utilized for LDAP or active directory with workstation clients)</li>
    <li style="color:white;">Integrates not just internally but externally via social login (GitHub, Facebook, Google, Twitter, OpenID)</li>
    <li style="color:white;">Built in security controls</li>
    <ul "list-style-type: circle">
      <li style="color:white;">Brute force protection</li>
      <li style="color:white;">Clickjacking protection</li>
    </ul>
  </ul>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: center, middle

<span style="color:white">
  <strong>Assurance Claims</strong>
</span>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: middle

<br>
<ol>
  <li style="color:white;">User credentials are transmitted to third party applications over secure channels.</li>
  <li style="color:white;">Stored user credentials are protected from unauthorized access.</li>
  <li style="color:white;">Sanitizing the input values from adding a new user minimizes the possibility of maliciously affecting Keycloak.</li>
  <li style="color:white;">Keycloak minimizes non-administrative users access to the server admin console.</li>
  <li style="color:white;">Keycloak is protected against brute force attacks.</li>
</ol>
<a href="https://www.lucidchart.com/documents/view/ba3f2ae5-7929-458f-850b-925295860062"><strong>Lucidchart diagrams</strong>   </a>
    
.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: center, middle

<span style="color:white">
  <strong>Security Requirements</strong>
</span>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: middle

<a href="https://www.lucidchart.com/documents/view/e31604af-862d-434b-a74c-e7850cc35a5d"><strong>Misuse Cases</strong></a>
<ul>
  <li style="color:white;">Misuse Case 1 elaborates on Assurance Case 1.</li>
  <li style="color:white;">Misuse Case 2 elaborates on Assurance Case 2.</li>
  <li style="color:white;">Misuse Case 3 elaborates on the combination of Assurance Cases 3 and 4.</li>
  <li style="color:white;">Misuse Case 4 elaborates on Assurance Case 5.</li>
</ul>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: middle

<br><br>
<a href="https://daniellucier.github.io/CYBER8420-SemesterProject/ThreatModels/TMT2016Docs/Keycloak-Threat-Model.htm"><strong>Threat Models</strong></a>
<ul>
  <li style="color:white;">Since Keycloak cannot ensure the security of each of the external interactors, a single trust boundary has been placed around the Keycloak process to fully protect the main process.</li>
  <li style="color:white;">All I/O should be scrubbed for any code that would negatively affect the Authentication Request/Response.</li> 
  <li style="color:white;">The Keycloak community has worked on securing the data flow between the process and the external interactor.</li>
  <li style="color:white;">The community has shown that the SSL/HTTPS mode mitigates spoofing attempts.</li>
</ul>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: center, middle

<span style="color:white">
  <strong>Code Review</strong>
</span>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: middle

<ul>
  <li style="color:white;">Based on risk based review</li>
  <li style="color:white;">Automatic static review</li>
   <ul "list-style-type: circle">
     <li style="color:white;">Sonar</li>
     <li style="color:white;">PMD</li>
  </ul>
  <li style="color:white;">Manual code review</li>
  <ul "list-style-type: circle">
    <li style="color:white;">Based on known CVE’s</li>
    <li style="color:white;">Reviewed the code changes that were implemented to fix the CVE’s</li>
  </ul>
</ul>
  
.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: center, middle

.center-image[![SonarFindings](https://daniellucier.github.io/CYBER8420-SemesterProject/CodeAnalysis/SonarKeyCloakFindings.PNG)]

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: center, middle

<span style="color:white">
  <strong>Contributions</strong>
</span>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

---
class: middle

<ul>
  <li style="color:white;">Potential staring points:</li>
  <ul "list-style-type: circle">
    <li style="color:white;">218 "blockers" found using Sonar</li>
    <li style="color:white;">Multiple "Law of Demeter" violations found using PMD</li>
    <ul "list-syle-type: circle">
      <li style="color:white;">See notes for definitions</li>
    </ul>
  </ul>
  <li style="color:white;">Fear of changes</li>
  <ul "list-style-type: circle">
    <li style="color:white;">255 unit tests</li>
    <li style="color:white;">0% Code Coverage</li>
  </ul>
</ul>

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]

???
Blocker (Sonar) = <a href="https://docs.sonarqube.org/display/SONAR/Issues">.red["Bug with a high probability to impact the behavior of the application in production: memory leak, unclosed JDBC connection, .... The code MUST be immediately fixed."]</a>

Law of Demeter (PMD) = Principle of Least Knowledge, <a href="http://pmd.sourceforge.net/pmd-5.0.1/rules/java/coupling.html">.red["It helps to reduce coupling between classes or objects."]</a>
---
class: center, middle

.center-image[![questions](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/questions.png)]

.bottom-left[![logo](https://daniellucier.github.io/CYBER8420-SemesterProject/misc/slides/images/keycloak_logo.png)]



    



