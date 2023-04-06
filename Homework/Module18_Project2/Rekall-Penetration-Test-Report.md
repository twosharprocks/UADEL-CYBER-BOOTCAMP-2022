
# Rekall Corporation
## Penetration Test Report



## Confidentiality Statement

This document contains confidential and privileged information from Rekall Inc. (henceforth known as Rekall). The information contained in this document is confidential and may constitute inside or non-public information under international, federal, or state laws. Unauthorized forwarding, printing, copying, distribution, or use of such information is strictly prohibited and may be unlawful. If you are not the intended recipient, be aware that any disclosure, copying, or distribution of this document or its parts is prohibited.


## Contact Information


<table>
  <tr>
   <td><strong>Company Name</strong>
   </td>
   <td>Two Sharp Rocks, LLC
   </td>
  </tr>
  <tr>
   <td><strong>Contact Name</strong>
   </td>
   <td>Josh Richards
   </td>
  </tr>
  <tr>
   <td><strong>Contact Title</strong>
   </td>
   <td>Penetration Tester
   </td>
  </tr>
</table>



## Document History


<table>
  <tr>
   <td><strong>Version</strong>
   </td>
   <td><strong>Date</strong>
   </td>
   <td><strong>Author(s)</strong>
   </td>
   <td><strong>Comments</strong>
   </td>
  </tr>
  <tr>
   <td>001
   </td>
   <td>06/4/2023
   </td>
   <td>Josh Richards
   </td>
   <td>Initial Report
   </td>
  </tr>
</table>


## Introduction

In accordance with Rekall policies, our organization conducts external and internal penetration tests of its networks and systems throughout the year. The purpose of this engagement was to assess the networks’ and systems’ security and identify potential security flaws by utilizing industry-accepted testing methodology and best practices.

For the testing, we focused on the following:



* Attempting to determine what system-level vulnerabilities could be discovered and exploited with no prior knowledge of the environment or notification to administrators.
* Attempting to exploit vulnerabilities found and access confidential information that may be stored on systems.
* Documenting and reporting on all findings.

All tests took into consideration the actual business processes implemented by the systems and their potential threats; therefore, the results of this assessment reflect a realistic picture of the actual exposure levels to online hackers. This document contains the results of that assessment.


### Assessment Objective

The primary goal of this assessment was to provide an analysis of security flaws present in Rekall’s web applications, networks, and systems. This assessment was conducted to identify exploitable vulnerabilities and provide actionable recommendations on how to remediate the vulnerabilities to provide a greater level of security for the environment.

We used our proven vulnerability testing methodology to assess all relevant web applications, networks, and systems in scope. 

Rekall has outlined the following objectives:

Table 1: Defined Objectives


<table>
  <tr>
   <td><strong>Objective</strong>
   </td>
  </tr>
  <tr>
   <td>Find and exfiltrate any sensitive information within the domain.
   </td>
  </tr>
  <tr>
   <td>Escalate privileges.
   </td>
  </tr>
  <tr>
   <td>Compromise several machines.
   </td>
  </tr>
</table>



## Penetration Testing Methodology


### Reconnaissance

We begin assessments by checking for any passive (open source) data that may assist the assessors with their tasks. If internal, the assessment team will perform active recon using tools such as Nmap and Bloodhound.


### Identification of Vulnerabilities and Services

We use custom, private, and public tools such as Metasploit, hashcat, and Nmap to gain perspective of the network security from a hacker’s point of view. These methods provide Rekall with an understanding of the risks that threaten its information, and also the strengths and weaknesses of the current controls protecting those systems. The results were achieved by mapping the network architecture, identifying hosts and services, enumerating network and system-level vulnerabilities, attempting to discover unexpected hosts within the environment, and eliminating false positives that might have arisen from scanning. 


### Vulnerability Exploitation

Our normal process is to both manually test each identified vulnerability and use automated tools to exploit these issues. Exploitation of a vulnerability is defined as any action we perform that gives us unauthorized access to the system or sensitive data. 


### Reporting

Once exploitation is completed and the assessors have completed their objectives, or have done everything possible within the allotted time, the assessment team writes the report, which is the final deliverable to the customer.


## Scope

Prior to any assessment activities, Rekall and the assessment team will identify targeted systems with a defined range or list of network IP addresses. The assessment team will work directly with the Rekall POC to determine which network ranges are in-scope for the scheduled assessment. 

It is Rekall’s responsibility to ensure that IP addresses identified as in-scope are actually controlled by Rekall and are hosted in Rekall-owned facilities (i.e., are not hosted by an external organization). In-scope and excluded IP addresses and ranges are listed below. 


<table>
  <tr>
   <td><strong>IP Address/URL</strong>
   </td>
   <td><strong>Description</strong>
   </td>
  </tr>
  <tr>
   <td>192.168.14.35
<p>
34.102.136.180 (totalrekall.xyz)
<p>
github.com/totalrekall
<p>
192.168.13.0/24
<p>
172.22.117.0/24
   </td>
   <td>Rekall public website
<p>
Rekall public domain name
<p>
Rekall public GitHub account
<p>
Internal domain range (Linux)
<p>
Internal domain range (Windows)
   </td>
  </tr>
</table>



# 


## Executive Summary of Findings


### Grading Methodology

Each finding was classified according to its severity, reflecting the risk each such vulnerability may pose to the business processes implemented by the application, based on the following criteria:

**Critical**:	 Immediate threat to key business processes.

**High**:		 Indirect threat to key business processes/threat to secondary business processes.

**Medium**:	 Indirect or partial threat to business processes. 

**Low**:		 No direct threat exists; vulnerability may be leveraged with other vulnerabilities.

Informational:    No threat; however, it is data that may be used in a future attack.

As the following grid shows, each threat is assessed in terms of both its potential impact on the business and the likelihood of exploitation:



![risk-matrix](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module16-17_Penetration-Testing/Images/Risk-Matrix.jpg?raw=true)

### 


### Summary of Strengths

While the assessment team was successful in finding several vulnerabilities, the team also recognized several strengths within Rekall’s environment. These positives highlight the effective countermeasures and defenses that successfully prevented, detected, or denied an attack technique or tactic from occurring. 



* Partial input validation for Javascript fields on web app
* Partial file whitelisting for uploads on web app
* Partial user authentication for restricted area on web app
* Webpage headers mostly sanitised of sensitive information
* Difficult to directory traverse to old disclaimers on web app
* IP lookup is relatively anonymous 
* Linux hosts have very few open ports
* “shadow” file is protected on all Linux hosts
* “passwd” file is protected on some Linux hosts 
* “sudoers” file is protected on some linux hosts
* Windows passwords are protected by NTLM
* Domain controller cannot be reached from outside internal network


### Summary of Weaknesses

We successfully found several critical vulnerabilities that should be immediately addressed to prevent an adversary from compromising the network. These findings are not specific to a software version but are more general and systemic vulnerabilities.



* No SSL certificate for public websites
* Numerous XSS, SQL, and Command injections possible on web application
* Cleartext user credentials stored in publicly available files
* Cleartext administrator credentials openly published next to login fields
* User credentials published on public code repositories
* Sensitive information in public website headers
* SSH usernames published in public domain registrar data
* Unpatched versions of server services with well-known vulnerabilities and numerous exploits
* Unpatched versions of core Linux commands
* Vulnerable and insecure FTP service
* Unprotected Windows system processes 
* Unprotected Windows domain control processes




## Executive Summary


### Day One - Web App

Initial reconnaissance of 192.168.14.35 was performed using a dictionary attack with dirbuster to establish a directory tree for the website and reveal hidden pages or files not linked directly on the public-facing website (T1590: Gather Victim Network Information). 

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/1-1-Dirbuster-initial.jpg)


Image 1-1.1 - OWASP Dirbuster performing a dictionary attack on 192.168.14.35

Due to the brute-force nature of Dirbuster, it was allowed to map the files and directories of 192.168.14.35 in the background as other access attempts were made. 

Navigating to “Welcome” (192.168.14.35/Welcome.php) the user is presented with a “Welcome to VR Planning” page. This page included a Javascript form intended for customers to enter their name which proved vulnerable to a reflected XSS attack (T1189: Drive-By Compromise).

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/2-1-WelcomeXSS.jpg)

Image 1-2.1 - “Welcome” with malicious XSS in Javascript entry field


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/2-2-WelcomeXSS.jpg)

Image 1-2.2 - Sensitive data (FLAG 1) displayed on Welcome.php after a reflected XSS attack

Navigating to “VR Planner” (192.168.14.35/Memory-Planner.php) the user is presented with a page with another Javascript entry field (“Choose your charachter” _[sic]_) and two opportunities for external file upload (“Choose your Adventure” and “Choose your location”). The “Choose your charachter” _[sic]_ form used some input validation, but still proved vulnerable to a reflected XSS attack (T1189: Drive-By Compromise) through script obfuscation with &lt;sscript> instead of &lt;script>.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/2-3-ssscriptXSS.jpg)

Image 1-2.3 - “Memory-Planner.php” with obfusated & malicious script in Javascript entry field

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/2-4-ssscriptXSS.jpg)

Image 1-2.4 - Sensitive data (flag 2) displayed on “Memory-Planner.php” after a reflected XSS attack

The two opportunities to upload files from the “Memory-Planner.php” page also opened the page up for potential Local File Inclusion attack (T1190: Exploit Public-Facing Application). The first upload opportunity (“Choose your Adventure”, shown below in Image 2.5) had no file whitelisting measures in place, and allowed the upload of a malicious php file instead of an image. This malicious php file revealed further sensitive data as “flag 5”.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/2-5-LFI.jpg)

Image 1-2.5 - “Choose your Adventure” before upload of the malicious php file


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/2-6-LFI.jpg)

Image 1-2.6 - Sensitive data (flag 5) displayed on “Memory-Planner.php” after Local File Inclusion

The second opportunity for file upload (“Choose your location” shown below in Image 2.7) used input whitelisting to filter any file uploads that did not end in “.jpg”. However the same malicious php file could still be uploaded by adding “.jpg” to the end of the filename (T1190: Exploit Public-Facing Application) to reveal sensitive data in the form of “flag 6”


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/2-7-LFI2.jpg)


Image 1-2.7 - “Choose your location” before upload of malicious php file with a .jpg extension

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/2-8-LFI2.jpg)


Image 1-2.8 - Sensitive data (flag 6) displayed on “Memory-Planner.php” after Local File Inclusion

Moving from Memory-Planner.php to the “Login.php” page, the user is presented with four Javascript entry fields: two for regular users to login with their name and password, and two more for an admin to login with a separate username and password. The first pair of fields (for user login) was shown to be susceptible to SQL injection, with a password-less login achieved using the payload: ‘ OR 1=1-- -

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/3-1-SQLinj.jpg)


Image 1-3.1 - A malicious SQL string in the Username field of “Login.php”


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/3-2-SQLinj.jpg)


Image 1-3.2 - Successful execution of malicious SQL string to bypass user password authentication

Successful user login revealed sensitive data in the form of “flag 7”. However login could also be achieved using unencrypted user credentials in an unprotected XML file stored on the web app.

Running DirBuster since the start of the penetration testing activity had produced a directory tree for most the website, revealing numerous sensitive files openly available without user authentication. One of these files was the openly accessible “heroes.xml” stored in the “passwords” sub-directory, which stored credentials for six users in cleartext (T1552.001: Credentials In Files), all of which were used to legitimately login to Login.php (T1078.003: Valid Accounts) without potentially alerting an administrator to the use of SQL injection.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/3-2-XMLUsers.jpg)

Image 1-3.3 - Publicly-available “heroes.xml” file found by DirBuster, listing cleartext user credentials 


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/3-2-neo1.jpg)

Image 3.4 - Using valid user credentials found in “heroes.xml” to login legitimately

Moving down the Login.php page to the admin login fields, it was quickly discovered by simply highlighting the text around the login fields that legitimate administrator credentials were in cleartext (but coloured to match the background) next to the white text “Login:” and “Password”, as shown below in Image 3.5.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/3-5-Admin.jpg)


Image 1-3.5 - Admin credentials discovered by highlighting the text near the Admin login

Using the publicly-available Admin credentials, it was possible to login and reveal further sensitive data in the form of “flag 8” and a link to sensitive administrator networking tools.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/3-6-Admin.jpg)

Image 1-3.6 - Successful admin login revealing flag 8 & link to admin networking tools

Access to these networking tools is not limited to administrators however, as login is not required and networking.php had been previously revealed through DirBuster.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/3-7-Networking.jpg)


Image 1-3.7 - DirBuster highlighting networking.php and “200” (OK) response

Likewise, DirBuster revealed two other sensitive cleartext files stored in the home directory of 192.168.14.35 - “robots.txt” and “vendors.txt”. “vendors.txt” revealed important server configuration information, while “robots.txt” revealed an un-indexed page “souvenirs.php” (previously identified by DirBuster) and “flag 9”.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/4-1-Robots.jpg)

Image 1-4.1 - Contents of robots.txt revealing unindexed page souvenirs.php and “flag 9”

Moving to the networking tools at network.php, the user is presented with two Javascript entry fields for performing a DNS and MX Record Lookup respectively. The first field (“DNS Check”) was proven to be highly susceptible to OS injection by using the character ; as a line break followed by an OS command. In this way the system information (such as ifconfig) could be viewed, and using the payload “[www.example.com](www.example.com); cat vendors.txt” to access the previously viewed “vendors.txt” file also revealed flag 10.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/4-2-ifconfig.jpg)
 

Image 1-4.2 - Using OS injection on “DNS Check” of networking.php to reveal network interfaces, vendor information & flag 10

Like the “DNS Check”, the “MX Record Checker” field on networking.php was also vulnerable to OS injection. While “DNS Check” required ; to break the command, a similar result could be achieved in “MX Record Checker” by using a pipe to display files. Using a pipe to display vendors.txt also resulted in the display of flag 11.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/4-2-vendors.jpg)


Image 1-4.3 - Using OS injection in “MX Record Checker” to display vendors.txt and flag 11

With the ability to view files from the underlying operating system, it was possible to use the MX Record Checker field to traverse the server’s etc folder and list all the users in the “passwd” file.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/4-3-users.jpg)


Image 1-4.4 - Image 4.3 - Using OS injection and ../../ in “MX Record Checker” to show system users

Most of the “users” listed have a UID &lt; 1000 and as such are not user accounts. However the user “melina” is a user account with a home directory on the system, and as such is likely to be an administrator. Using this user account, it was then possible to guess the user’s weak password (“melina”) to again access the administrator section of the website. Using this second account it was possible to view flag 12, as well a link to a hidden part of the website. 

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/4-5-melina.jpg)


Image 1-4.5 - Using “melina:melina” to access the admin login and retrieve flag 12

Following the link to the “secret legal data” revealed “admin_legal_data.php” which is a page that DirBuster has **<span style="text-decoration:underline;">not</span>** previously identified. This page presented the user with a notice “This page is locked. Admins Only!” however the address bar showed “?admin=001” suggesting the page used weak cookies.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/5-1-admin.jpg)


Image 1-5.1 - admin_legal_data.php showing “admin=001” suggesting weak cookies for authentication

A Battering Ram attack was attempted on the page using BurpSuite Intruder by modifying the “admin=” value to test sequential numbers between 1 and 100.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/5-2-Ram-Payload.jpg)

Image 1-5.2 - Preparing a sequential number Battering Ram attack against “admin_legal_data.php”

Reviewing the results of the battering ram attack “87” was identified as the only payload with a different length to all others, and inspecting the server response revealed flag 14.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/5-2-Ram-Result.jpg)

Image 1-5.3 - Battering Ram attack results with payload 87’s different length and flag 14 in response

Reviewing missing flags and pages not previously inspected, we moved to comments.php where the user is presented with a Javascript field for adding comments to the page. This Javascript field was shown to be susceptible to Reflected XSS attacks via unsanitised user input (T1189: Drive-By Compromise).

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/6-1-Comments.jpg)

Image 1-6.1 - comments.php with a Reflected XSS payload in the Javascript field

Executing the payload &lt;script>alert(1)&lt;/script> resulted in an on-screen alert “1” and revealed flag 3.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/6-2-Comments.jpg)

Image 1-6.2 - comments.php after executing the XSS payload to show alert “1” and flag 3

Moving to souvenirs.php, the user is presented with a page offering merchandise and a link that prints “CALLUSNOW” when clicked. Inspecting the address bar it appears the website prints whatever is after “?message=” and is susceptible to command injection.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/6-3-Souvenirs.jpg)

Image 1-6.3 - souvenirs.php after clicking the on-screen link to display “CALLUSNOW”

Testing this page for command injection, it was found that ;system would reveal flag 13.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/6-4-Souvenirs.jpg)


Image 1-6.4 - Using the ;system payload in the address bar to reveal flag 13

Reviewing all discovered pages on 192.168.14.35, it was decided to inspect the headers of public-facing pages for sensitive information. Using curl to inspect the headers, it was shown that sensitive information in the form of “flag 4” could be found in the header of “About-Rekall.php” under the “X-Powered-By” section.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/7-1-CURL.jpg)

Image 1-7.1 - Using curl to inspect page headers, revealing Flag 4 in About-Rekall.php

Reviewing pages also revealed that disclaimer.php had not been previously investigated. Moving to “disclaimer.php” directly revealed no information, however navigating to it through the button on the “Welcome.php” page revealed the address needed to include ?page=disclaimer_2.txt to display a disclaimer. This suggested directory traversal may be possible.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/7-2-Disclaimer.jpg)


Image 1-7.2 - disclaimer.php using ?page=disclaimer_2.txt to display the current disclaimer

“disclaimer_2.txt”  suggested that a previous version may be accessible and likely named “disclaimer.txt” or “disclaimer_1.txt”. After attempting multiple variations, directory traversal was achieved to access “disclaimer_1.txt” in the “old_disclaimers” directory and reveal flag 15.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day1/7-3-Disclaimer.jpg)

Image 1-7.3 - Using directory traversal to display disclaimer_1.txt and flag 15


### Day Two - Linux Systems

The second day of the penetration test began with OSINT reconnaissance to support system scanning and eventual access. Performing a WHOIS domain lookup with “who.is” on the public-facing “totalrekall.xyz” domain name returned registrar data that included sensitive information including an ssh username and “flag1”.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag1-whoisregistrar.jpg)


Image 2-1.1 - Public registrar data on totalrekall.xyz showing ssh user “alice” and flag 1

Performing a similar lookup for IP address information on “totalrekall.xyz” using “iplocation.io” returned an IPv4 address (34.102.136.180 aka “flag 2”) as well as the ISP and an approximate location for the data centre (T1590.001 Gather Victim Network Information - IP Addresses).


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag2-iplookup.jpg)


Image 2-1.2 - Public IP address and lookup data for totalrekall.xyz

An SSL certificate search was also performed through “crt.sh” on “totalrekall.xyz” to identify sensitive data and identify “flag 3”


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag3-sslcert.jpg)


Image 2-1.3 - Public SSL certificate lookup on totalrekall.xyz revealing flag 3

With this OSINT collected, a Nmap scan of the 192.168.13.0/24 subnet was performed to identify available hosts and open ports on the Rekall internal network. This initial scan returned a total of 6 hosts, with 5 hosts belonging to Rekall’s internal network (192.168.13.10-14) and the 6th (192.168.13.1) belonging to the penetration tester.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag4-nmap.jpg)


Image 2-2.1 - Nmap scan of 192.168.13.0/24 revealing 5 Rekall hosts (192.168.13.10-14)

This initial Nmap scan only provided limited information on the host operating system, so it was repeated in a more aggressive mode to provide additional host information and potentially identify vulnerabilities for exploitation.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag5-nmap-aggressive.jpg)


Image 2-2.2 - Aggressive Nmap scan of 192.168.13.0/24 revealing additional host information

This second scan revealed 192.168.13.13 was running a version of Drupal 8 with a known vulnerability (CVE-2019-6340) in its content management system, making it susceptible to remote code execution.

The aggressive Nmap scan also reported potentially risky http methods being performed by the 192.168.13.12 host, so a Nessus scan was performed against it to identify vulnerabilities. This revealed a critical remote code execution vulnerability (ID 97610) in its version of Apache Struts.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag6-nessus.jpg)


Image 2-2.3 - Nessus scan on 192.168.13.12 revealing a critical vulnerability in Apache Struts

Reviewing the aggressive Nmap scan again, host 192.168.13.10 was shown to be running an Apache Tomcat/Coyote JSP engine on open port 8080 (TCP). Performing a metasploit search for “apache tomcat jsp” provided an exploit to upload a shell using a PUT request bypass (CVE-2017-12617), and this was used to create a command shell and access sensitive data.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag7-jspbypass-ip10.jpg)


Image 2-3.1 - Using a tomcat jsp exploit to establish a shell and access 192.168.13.10’s root folder

The aggressive Nmap scan also revealed host 192.168.13.11 is running Apache 2.4.7 - a version of Apache that is known to be vulnerable to “Shellshock” remote code execution through the bash shell’s evaluation of environment variables (CVE-2014-6271). By running the Shellshock exploit against 192.168.13.11 it was possible to achieve sudo access on the host to view the sudoers file.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag8-1-shellshock-11.jpg)


Image 2-3.2 - Setting up the Shellshock exploit to execute on 192.168.13.11


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag8-shellshock-sudoers.jpg)


Image 2-3.3 - Post-exploitation of 192.168.13.11 to view the sudoers file and reveal flag 8

Continued exploitation of 192.168.13.11 also revealed the host’s passwd file could be viewed.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag9-passwd-11.jpg)


Image 2-3.3 - Post-exploitation of 192.168.13.11 to view the passwd file and reveal flag 9

Taking advantage of the Apache Struts vulnerability (CVE-2017-5638) identified in the earlier Nessus scan of 192.168.13.12, an exploit was found that would take advantage of how Struts 2’s OGNL module managed HTTP content to execute code remotely and achieve a meterpreter shell.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag10-exploit-struts-ip12.jpg)


Image 2-3.4 - Running a Struts 2 exploit on 192.168.13.12 to establish a meterpreter session

 With Meterpreter access, a search for sensitive files was conducted and the compressed file “flagisinthisfile.7z” was identified for exfiltration and inspection to reveal flag 10.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag10-ip12.jpg)


Image 2-3.5 - Searching 192.168.13.12 for “flags” then viewing “flagisinthisfile.7z”

Moving to host 192.168.13.13, an attempt was made to exploit the vulnerability in Drupal 8 (CVE-2019-6340) that was previously identified by the aggressive Nmap scan. Using an unserialised PHP RCE exploit, it was possible to establish a Meterpreter session and determine the user ID.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag11-getuid-ip13.jpg)


Image 2-3.6 - Using a PHP exploit on 192.168.13.13 and determining the user ID

Finally, access to 192.168.13.14 was attempted using the open SSH port (22) identified in the aggressive Nmap scan. The WHOIS lookup on totalrekall.xyz have previously revealed an SSH user “alice” in the domain’s registrar data, so access with this username was attempted (T1110.001 Password Guessing).


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag12-alice-ssh-ip14.jpg)


Image 2-4.1 - Attempting SSH access to 192.168.13.14 with username “alice”

Automated password guessing was attempted using Hydra and the rockyou.txt wordlist, however the penetration tester guessed the user password “alice” in a separate terminal before Hydra was successful. 


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag12-alice-ssh-hydra-ip14.jpg)


Image 2-4.2 - Running an unsuccessful Hydra attack on 192.168.13.14’s SSH service


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag12-alice-success-ip14.jpg)


Image 2-4.3 - Successfully logging into 192.168.13.14’s SSH service using “alice:alice”

With user access to 192.168.13.14, the next step was to escalate privileges. Using a vulnerability in the sudoers configuration, it was possible to set the user ID as -1 to bypass sudo authentication and gain root privilege (CVE-2019-14287). With root privilege, it was then possible to navigate to the root folder and display the “flag12.txt” file.

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day2/flag12-alice-sudo-expl-ip14.jpg)


Image 2-4.4 - Gaining root privilege through a sudoers configuration vulnerability and viewing flag 12




### Day Three - Windows Systems

The third and final day of penetration testing began with an OSINT search for user credentials in the public repositories of the “totalrekall” account on GitHub. Accessing “[www.github.com/totalrekall](www.github.com/totalrekall)” only one public repository was available and labelled “site”. Opening this repository the majority of it appeared to be a backup of an old version of the Rekall corporation’s website.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day3/flag1-1gitrepo.jpg)


Image 3-1.1 - Publicly-available “site” repository on the “totalrekall” GitHub account

The “xampp.users” file stood out however, and opening it revealed a username “trivera” and password hash. 

![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day3/flag1-github.jpg)


Image 3-1.2 - The xampp.users file revealing a username and password hash

This password hash was immediately dropped into a text file and cracked using John the Ripper (T1110.002:Password Cracking) to reveal the password “Tanya4life”.


![alt_text](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module18_Project2/Images-Day3/flag1-pass.jpg)


Image 3-1.3 - Cracking the password hash for trivera

The next step was to run an aggressive Nmap scan on Rekall’s windows subnet 172.22.117.0/24 to identify any available hosts and any vulnerabilities for use in future exploitation.



<p id="gdcalert54" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image54.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert55">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image54.jpg "image_tooltip")


Image 3-2.1 - Running an aggressive Nmap scan against 172.22.117.0/24

This Nmap scan returned three hosts on the subnet, with two of them belonging to Rekall (172.22.117.10 & .20) and the third being the penetration tester’s machine (172.22.117.100). This scan also revealed that 172.22.117.10 was likely to be the Windows Domain Controller, while 172.22.117.20 appeared to be hosting an Apache http server, an anonymous FTP service, and a SLMail service.

Attacking the http service on 172.22.117.20 first, an attempt was made to access the site through a web browser. Entering the ip address into the browser prompted a username and password, so “trivera:Tanya4life” collected from the public Github repository was tested and succeeded in providing access.



<p id="gdcalert55" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image55.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert56">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image55.jpg "image_tooltip")


Image 3.2.2 - Login prompt on 172.22.117.20 with trivera’s credentials entered

Logging into 172.22.117.20 with trivera’s credentials provided sensitive information in the form of flag2.txt



<p id="gdcalert56" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image56.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert57">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image56.jpg "image_tooltip")


Image 3.2.3 - Successful login to 172.22.117.20 revealing cleartext file “flag2.txt”

Next the FTP service of 172.22.117.20 was evaluated. The aggressive Nmap scan had revealed that an anonymous login was possible and that file “flag3.txt” was available, so terminal was used to access the FTP service on 172.22.117.20 and download the file.



<p id="gdcalert57" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image57.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert58">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image57.jpg "image_tooltip")


Image 3-2.4 - Accessing the FTP service on 172.22.117.20 anonymously to retrieve flag3.txt

Next the SLMail service on 172.22.117.20 was attacked. Metasploit was searched for “slmail” with a single exploit (seattlelabs_pass) being returned that would exploit a buffer overflow vulnerability in Seattle Lab Mail 5.5 (CVE-2003-0264). 



<p id="gdcalert58" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image58.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert59">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image58.jpg "image_tooltip")


Image 3-2.5 - Searching for an exploit to use on 172.22.117.20’s SLMail service

After setting the options for the seattlelabs_pass exploit and successfully running it against 172.22.117.20, a meterpreter session was established and by listing files in the landing directory, flag4.txt was identified.



<p id="gdcalert59" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image59.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert60">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image59.jpg "image_tooltip")


Image 3-2.6 - Running the seattlelabs_pass exploit on 172.22.117.20 and identifying flag4.txt

With initial access to 172.22.117.20 established, the next step was to establish a persistent backdoor by identifying and manipulating a scheduled system task. Opening a shell in meterpreter, the existing scheduled system tasks were queried with a filter to identify potential tasks named “flag5” with as much information about them as possible. Results returned a scheduled task named “flag5” which contained sensitive information in the Comment section.



<p id="gdcalert60" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image60.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert61">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image60.jpg "image_tooltip")


Image 3-2.7 - Running a scheduled tasks query with task name “flag5” and the verbose list options

The next step was to enumerate the users of 172.22.117.20 by running the kiwi module against it. By dumping the Security Accounts Manager (SAM) database out with kiwi’s LSA_dump tool, the NTLM password hashes for users “sysadmin” and “flag6” were both identified.



<p id="gdcalert61" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image61.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert62">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image61.jpg "image_tooltip")


Image 3-2.8 - Dumping 172.22.117.20’s SAM database to reveal users and password hashes

Running John the Ripper against the password hashes revealed the “flag6” user’s password to be “Computer!”.



<p id="gdcalert62" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image62.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert63">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image62.jpg "image_tooltip")


Image 3-2.9 - Cracking the password hash for user “flag6”

Searching 172.22.117.20 for more sensitive information, a shell was established in meterpreter before searching through the host’s public user documents for sensitive information. 



<p id="gdcalert63" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image63.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert64">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image63.jpg "image_tooltip")


Image 3-2.10 - Listing the files in C:\Users\Public\Documents and identifying “flag7.txt”

Next a lateral move from the 172.22.117.20 host to the Domain Controller 172.22.117.10 was attempted. To access 172.22.117.10 a domain administrator password would be needed, so the kiwi module was again used but this time to dump the LSA cache using “lsadump::cache”.



<p id="gdcalert64" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image64.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert65">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image64.jpg "image_tooltip")


Image 3-3.1 - Using lsadump::cache to dump administrator credentials (password hash highlighted)

Cracking the MsCacheV2 password hash for domain administrator “ADMBob” in John the Ripper produced the password “Changeme!”. Using these domain administrator credentials and the SMBDomain “rekall”, it was then possible to use the psexec exploit to establish a meterpreter session on the 172.22.117.10 domain controller from the previously exploited 172.22.117.20 host. 

Using this meterpreter session, it was then possible to create a shell and list user accounts to identify flag8.



<p id="gdcalert65" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image65.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert66">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image65.jpg "image_tooltip")


Image 3-3.2 - Using the psexec exploit to establish a meterpreter session on 172.22.117.10 before enumerating the network users.

Navigating through the shell to the C:\, all the files in the root directory were listed to reveal “flag9.txt”



<p id="gdcalert66" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image66.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert67">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image66.jpg "image_tooltip")


Image 3-3.3 - Navigating to C:\ to find and display flag9.txt

With meterpreter shell access to 172.22.117.10, it was then straight-forward to use the kiwi module to perform “dcsync_ntlm” to simulate the Domain Controller and pull the administrator’s NTLM password hash.



<p id="gdcalert67" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image67.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert68">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image67.jpg "image_tooltip")


Image 3-3.4 - Pulling the administrator’s NTLM hash from 172.22.117.10 with kiwi and dcsync_ntlm




## Summary Vulnerability Overview


<table>
  <tr>
   <td><strong>Vulnerability</strong>
   </td>
   <td><strong>Severity</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - No valid SSL certificate for public web application
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Reflected XSS on public web application
   </td>
   <td><strong>High</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Local File Inclusion on public web application
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Cleartext credentials stored on public web application
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Network security details stored on public web application
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - OS injection in publicly-available network security tools
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Weak administrator passwords on public web application
   </td>
   <td><strong>High</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Administrator credentials stored on publicly-available page
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Command injection on public web application
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Sensitive information stored in headers of web application
   </td>
   <td><strong>Low</strong>
   </td>
  </tr>
  <tr>
   <td>Web App - Directory traversal to sensitive documents on web application
   </td>
   <td><strong>High</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Sensitive information in domain registrar data
   </td>
   <td><strong>Low</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Sensitive information in domain IP lookup
   </td>
   <td><strong>Low</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Sensitive information in domain SSL certificate search 
   </td>
   <td><strong>Low</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Tomcat JSP upload bypass on Linux host
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Vulnerable Apache version on Linux host
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Vulnerable Apache Struts version on Linux host
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Vulnerable Drupal version on Linux host
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Weak SSH password on Linux host
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Linux - Vulnerable Sudo version on Linux host
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - User credentials stored on public code repository
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Anonymous FTP access on Windows host
   </td>
   <td><strong>High</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Vulnerable SLMail version on Windows host
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Unprotected Windows System Process (schtasks)
   </td>
   <td><strong>Medium</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Unprotected Windows System Process (SAM)
   </td>
   <td><strong>High</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Sensitive information in public documents on Windows host
   </td>
   <td><strong>Medium</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Unprotected Windows System Process (LSA)
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Unprotected Windows System Process (PsExec)
   </td>
   <td><strong>High</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Sensitive information in Windows root directory
   </td>
   <td><strong>Medium</strong>
   </td>
  </tr>
  <tr>
   <td>Windows - Unprotected domain controller process (dcsync)
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
</table>


The following summary tables represent an overview of the assessment findings for this penetration test:


<table>
  <tr>
   <td><strong>Scan Type</strong>
   </td>
   <td><strong>Total</strong>
   </td>
  </tr>
  <tr>
   <td>Hosts
   </td>
   <td>192.168.14.35, 192.168.13.10, 192.168.13.11, 192.168.13.12, 192.168.13.13, 192.168.13.14
<p>
172.22.117.20, 172.22.117.10
<p>
34.102.136.180
   </td>
  </tr>
  <tr>
   <td>Ports
   </td>
   <td>1-1000
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong>Exploitation Risk</strong>
   </td>
   <td><strong>Total</strong>
   </td>
  </tr>
  <tr>
   <td><strong>Critical</strong>
   </td>
   <td>17
   </td>
  </tr>
  <tr>
   <td><strong>High</strong>
   </td>
   <td>6
   </td>
  </tr>
  <tr>
   <td><strong>Medium</strong>
   </td>
   <td>3
   </td>
  </tr>
  <tr>
   <td><strong>Low</strong>
   </td>
   <td>4
   </td>
  </tr>
</table>





## Vulnerability Findings


### No Valid SSL Certificate for Public Web Application

**Risk Rating**: **Critical**

**Description**: 

The domains **192.168.14.35 **and **34.102.136.180 (totalrekall.xyz)** are public-facing sites for Rekall Corporation. Neither of these web domains use valid SSL certificates, with all traffic to and from them being transmitted insecurely through the HTTP protocol. Without a valid SSL certificate, these domains allow malicious packet-sniffing and manipulation with the potential for Man-in-the-Middle attacks

**Affected Hosts**: 192.168.14.35, 34.102.136.180

**Remediation**: 



* Generate and implement SSL certificates from a trusted certificate authority


### Reflected XSS on Public Web Application

**Risk Rating**: **High**

**Description**: 

The webpages **192.168.14.35/welcome.php, 192.168.14.35/Memory-planner.php,** and **192.168.14.35/comments.php** are public-facing pages for Rekall Corporation. These three pages feature multiple Javascript fields that allow a malicious user to extract information from the server using a reflected XSS attack (T1189: Drive-By Compromise).

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Sanitise and validate all user input
* Encode and validate all server output
* Implement a Web Application Firewall (WAF)


### SQL Injection through User Login on Public Web Application

**Risk Rating**: **Critical**

**Description**: 

The webpage **192.168.14.35/Login.php** is a public-facing page for Rekall Corporation for user and administrator login. This page features two fields for user-level login which are vulnerable to malicious SQL payloads that allow an unauthenticated user to log in without a password (T1190: Exploit Public-Facing Application).

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Sanitise and validate all user input
* Use prepared/parameterised statements for input fields 
* Limit login attempts to mitigate brute force attacks
* Implement a Web Application Firewall (WAF)


### Cleartext credentials stored on Public Web Application

**Risk Rating**: **Critical**

**Description**: 

The webpage **192.168.14.35/passwords/heroes.xml** is a publicly accessible XML file. This file lists user credentials in clear text for six different users (T1552.001: Credentials In Files), all of which can be used to access the user login at 192.168.14.35/Login.php (T1078.003: Valid Accounts)

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Remove all files that store user credentials in cleartext


### Network security details stored on Public Web Application

**Risk Rating**: **Critical**

**Description**: 

The webpage **192.168.14.35/vendors.txt** is a publicly-accessible TXT file. This file lists confidential server information (T1589.006: Gather Victim Network Information - Network Security Appliances) in cleartext, all of which can be used to avoid or bypass network security systems (TA0005: Defense Evasion)

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Remove all publicly-accessible files which contain server or network information.


### OS injection in publicly-available network security tools

**Risk Rating**: **Critical**

**Description**: 

The webpage **192.168.14.35/networking.php** is a publicly-accessible webpage for Rekall Corporation. This page contains confidential tools for testing network infrastructure, which also allow for OS injection attacks to reveal server information and network security (T1589.006: Gather Victim Network Information - Network Security Appliances).

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Implement SSL throughout the domain
* Secure admin-only pages that feature confidential network infrastructure and security information.


### Weak administrator passwords on Public Web Application

**Risk Rating**: **High**

**Description**: 

The webpage **192.168.14.35/Login.php** is a public-facing page for Rekall Corporation for user and administrator login. This page features two fields for administrator-level login which is vulnerable to password guessing due to weak administrator passwords (T1110.001: Brute Force - Password Guessing).

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Implement strong password policy, especially requiring password does not match username
* Limit login attempts to mitigate brute force attacks
* Implement a Web Application Firewall (WAF)
* Reset administrator password for **melina**


### Administrator credentials stored on publicly-available page

**Risk Rating**: **Critical**

**Description**: 

The webpage **192.168.14.35/Login.php** is a public-facing page for Rekall Corporation for user and administrator login. This page features two fields for administrator-level login, both of which feature an administrator-level username and matching password (T1078.003: Valid Accounts) right next to the relevant field, and are viewable by highlighting the login area or from the page source.

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Implement strong password policy
* Remove all publicly-viewable user and administrator credentials
* Limit login attempts to mitigate brute force attacks
* Implement a Web Application Firewall (WAF)
* Reset administrator password for **dougquaid**


### Weak authentication on restricted area of web application

**Risk Rating**: **Critical**

**Description**: 

The webpage **192.168.14.35/admin_legal_data.php** is a public-facing page for Rekall Corporation which displays legal documents to authenticated users. This page uses weak authentication which can be overridden through brute forcing session identifiers.

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Secure documents by requiring two-factor authentication
* Limit GET requests to admin_legal_data.php to mitigate brute force attacks
* Implement strong cookie policies to prevent easily predicted session identifiers


### Command injection on public web application

**Risk Rating**: **Critical**

**Description**: 

The webpage **192.168.14.35/souvenirs.php** is an un-indexed, public-facing page for Rekall Corporation. This page features a message system that allow a malicious user to injection system commands into the server to extract host information and perform unauthorised actions (T1189: Drive-By Compromise).

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Remove weak session identifiers
* Sanitise and validate all user requests
* Encode and validate all server output
* Implement a Web Application Firewall (WAF)


### Sensitive information stored in headers of web application

**Risk Rating**: **Low**

**Description**: 

The webpage **192.168.14.35/About-Rekall.php** is a public-facing page for Rekall Corporation. This page contains sensitive information in the page header (T1594: Search Victim-Owned Websites) and could be leveraged with other vulnerabilities.

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Remove all sensitive information from webpage headers.


### Directory traversal to sensitive documents on web application

**Risk Rating**: **High**

**Description**: 

The webpage **192.168.14.35/disclaimer.php** is a public-facing page for Rekall Corporation. This page is vulnerable to directory traversal and can reveal sensitive information in the form of old disclaimers if an attacker guesses the predictable directory structure and predictable filename (T1189: Drive-By Compromise)

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Remove all sensitive information from publicly-available web applications
* Sanitise and validate all user requests




### Sensitive information in domain registrar data

**Risk Rating**: **Low**

**Description**: 

The webpage **totalrekall.xyz** is a publicly-listed domain name for Rekall Corporation. The WHOIS domain lookup information for this page reveals sensitive information (T1590.001: Gather Victim Network Information - Domain properties), including an SSH username for an internal Rekall network.

**Affected Hosts**: totalrekall.xyz (34.103.136.180)

**Remediation**: 



* Remove all sensitive information from domain name’s WHOIS registrar. 


### Sensitive information in domain IP lookup

**Risk Rating**: **Low**

**Description**: 

The webpage **totalrekall.xyz** is a publicly-listed domain name for Rekall Corporation. The WHOIS domain lookup information for this page reveals sensitive information (T1590.001: Gather Victim Network Information - Domain properties), including hosting information and potential physical address.

**Affected Hosts**: totalrekall.xyz (34.103.136.180)

**Remediation**: 



* Remove all sensitive information from domain name’s IP lookup. 


### Sensitive information in domain SSL certificate search

**Risk Rating**: **Low**

**Description**: 

The webpage **totalrekall.xyz** is a publicly-listed domain name for Rekall Corporation. The SSL certificate lookup information for this page reveals sensitive information (T1590.001: Gather Victim Network Information - Domain properties), including certificate validity, certificate issuer, and related domains.

**Affected Hosts**: totalrekall.xyz (34.103.136.180)

**Remediation**: 



* Remove all sensitive information from domain name’s SSL certificate. 


### Tomcat JSP upload bypass on Linux host

**Risk Rating**: **Critical**

**Description**: 

The host 192.168.13.10 is a Rekall host running Apache Tomcat/Coyote JSP on open port 8080. This configuration is known to be vulnerable to a JSP upload bypass that uses a malicious HTTP PUT request to execute an exploit that establishes a command shell with root access on the host.

**Affected Hosts**: 192.168.13.10

**Remediation**: 



* Restrict the use of HTTP PUT commands to the server
* Close port 8080
* Update Server-side code detection to identify JSP exploit signatures


### Vulnerable Apache version on Linux host

**Risk Rating**: **Critical**

**Description**: 

The host 192.168.13.11 is a Rekall host running Apache 2.4.7. This version of Apache is known to be vulnerable to “Shellshock” remote code execution (CVE-2014-6271) which can be exploited to establish a command shell with sudo access on the host.

**Affected Hosts**: 192.168.13.11

**Remediation**: 



* Update Apache to 2.4.56 (latest version at the time of writing)
* Update Bash to 5.2.15 (latest version at the time of writing)
* Sanitise and encode user input


### Vulnerable Apache Struts version on Linux host

**Risk Rating**: **Critical**

**Description**: 

The host 192.168.13.12 is a Rekall host running Apache Struts 2. This version of Struts is known to be vulnerable to remote code execution through the OGNL module’s management of HTML (CVE-2017-5638) which can be exploited to establish a command shell on the host.

**Affected Hosts**: 192.168.13.12

**Remediation**: 



* Update Apache Struts to 6.1.2 (latest version at the time of writing)


### Vulnerable Drupal version on Linux host

**Risk Rating**: **Critical**

**Description**: 

The host 192.168.13.13 is a Rekall host running Drupal 8. This version of Drupal is known to be vulnerable to remote code execution through insufficient input sanitisation (CVE-2019-6340) which can be exploited using malicious PHP code to establish a command shell on the host.

**Affected Hosts**: 192.168.13.13

**Remediation**: 



* Update Drupal to 10.0.7 (latest version at the time of writing)
* Sanitise user input


### Weak SSH password on Linux host

**Risk Rating**: **Critical**

**Description**: 

The host 192.168.13.14 is a Rekall host running an SSH service on port 22. Using a publicly-available username, this service is vulnerable to password guessing due to a weak administrator password (T1110.001: Brute Force - Password Guessing).

**Affected Hosts**: 192.168.14.35

**Remediation**: 



* Implement strong password policy, especially requiring password does not match username
* Limit login attempts to mitigate brute force attacks
* Change SSH to non-default port
* Reset SSH password for **alice**


### Vulnerable Sudo version on Linux host

**Risk Rating**: **Critical**

**Description**: 

The host 192.168.13.14 is a Rekall host running a version of Sudo before 1.8.28. Versions of Sudo before 1.8.28 are known to be vulnerable to a sudoers authentication bypass (CVE-2019-14287) which will elevate user privileges to root.

**Affected Hosts**: 192.168.13.14

**Remediation**: 



* Update Sudo to 1.9.13 (latest version at the time of writing)
* Configure sudoers file to ensure that root is not excluded in “runas” specifications


### User credentials stored on public code repository

**Risk Rating**: **Critical**

**Description**: 

The GitHub account “totalrekall” is a Rekall repository storing a backup of the public website. This repository includes a “xampp.users” file which contains a username and password hash, which can be cracked and used to access restricted web content.

**Affected Hosts**: https://github.com/totalrekall/site

**Remediation**: 



* Remove “xampp.users”
* Remove public “site” repository and replace with a private repository
* Reset password for **trivera**


### Anonymous FTP access on Windows host

**Risk Rating**: **Critical**

**Description**: 

The host 172.22.117.20 is a Rekall host running an FTP service on port 21. The FTP service is configured to accept anonymous access without credentials, allowing the download of un sensitive information. 

**Affected Hosts**: 172.22.117.20

**Remediation**: 



* Implement sFTP with a strong password policy for authorised users
* Limit login attempts to mitigate brute force attacks
* Reset SSH password for **alice**


### Vulnerable SLMail version on Windows host

**Risk Rating**: **Critical**

**Description**: 

The host 172.22.117.20 is a Rekall host running a SLMail 5.5 service on ports 25, 106 and 110. This version of SLMail is known to be vulnerable to numerous remote code execution exploits, notably through a POP3 buffer overflow (CVE-2003-0264) which can be exploited to establish a command shell on the host. 

**Affected Hosts**: 172.22.117.20

**Remediation**: 



* Replace SLMail with alternative email server software
* Close ports 25, 106 and 110


### Unprotected Windows System Process (schtasks)

**Risk Rating**: **Medium**

**Description**: 

The host 172.22.117.20 is a Rekall host running Windows. With initial access to a Windows host, and attacker can access systems processes and establish a malicious scheduled task which will provide a persistent backdoor unless removed.

**Affected Hosts**: 172.22.117.20

**Remediation**: 



* Regularly update Windows and implement security patches
* Regularly check scheduled tasks on Windows hosts to identify unusual/malicious entries
* Update end-point protection systems to identify C2 and scheduled task exploit signatures


### Unprotected Windows System Process (SAM)

**Risk Rating**: **High**

**Description**: 

The host 172.22.117.20 is a Rekall host running Windows. With initial access to a Windows host, an attacker can access systems processes and dump the Security Account Manager database to access NTLM hashes for local users.

**Affected Hosts**: 172.22.117.20

**Remediation**: 



* Regularly update Windows and implement security patches
* Implement strong password policy for all users
* Update end-point protection systems to identify Mimikatz/Kiwi exploit signatures


### Sensitive information in public documents on Windows host

**Risk Rating**: **Medium**

**Description**: 

The host 172.22.117.20 is a Rekall host running Windows. With initial access to a Windows host, an attacker can access documents stored in the “Public” folder and reveal sensitive information saved there.

**Affected Hosts**: 172.22.117.20

**Remediation**: 



* Encrypt sensitive documents and store them in protected directories


### Unprotected Windows System Process (LSA)

**Risk Rating**: **Critical**

**Description**: 

The host 172.22.117.20 is a Rekall host running Windows. With initial access to a Windows host, an attacker can access systems processes and dump the LSA cache to access NTLM hashes for domain administrators.

**Affected Hosts**: 172.22.117.20

**Remediation**: 



* Enable LSA Protection on Windows
* Regularly update Windows and implement security patches
* Implement strong password policy for all users
* Implement network segmentation
* Update end-point protection systems to identify Mimikatz/Kiwi exploit signatures


### Unprotected Windows System Process (PsExec)

**Risk Rating**: **Medium**

**Description**: 

The hosts 172.22.117.10 and 172.22.117.20 are Rekall hosts running Windows. With initial access to an internal Windows host, an attacker can elevate non-admin processes to system-level (CVE-2021-1733) and allow lateral network movement, system persistence, and malicious code execution with administrator privileges.

**Affected Hosts**: 172.22.117.20 and 172.22.117.20

**Remediation**: 



* Enable LSA Protection on Windows
* Regularly update Windows and implement security patches
* Implement strong password policy for all users
* Implement network segmentation
* Update end-point protection systems to identify Mimikatz/Kiwi exploit signatures


### Sensitive information in Windows root directory

**Risk Rating**: **Medium**

**Description**: 

The host 172.22.117.10 is a Rekall host running Windows. With initial access to this host through lateral movement from 172.22.117.20, an attacker can access documents stored in the C:\ root directory and reveal sensitive information saved there.

**Affected Hosts**: 172.22.117.10

**Remediation**: 



* Encrypt sensitive documents and store them in protected directories


### Unprotected domain controller process (dcsync)

**Risk Rating**: **Critical**

**Description**: 

The host 172.22.117.20 is a Rekall host running Windows. With initial access to this host through lateral movement from 172.22.117.20, an attacker can request domain administrator credentials from the domain controller and crack the returned NTLM hash for full domain administrator credentials.

**Affected Hosts**: 172.22.117.10

**Remediation**: 



* Regularly update Windows and implement security patches
* Implement strong password policy for all users
* Update end-point protection systems to identify Mimikatz/Kiwi exploit signatures
* Remove unusual accounts with replication permissions
* Restrict user replication permissions




## MITRE ATT&CK Navigator Map

The following completed MITRE ATT&CK navigator map shows all of the techniques and tactics that TSR used throughout the assessment.

A complete version of this MITRE ATT&CK Navigator Map is also [available as a JSON](https://drive.google.com/file/d/1gOJL5aP9MkefX5xS4p6epdFcto5NmqzN/view?usp=sharing) or as a [standalone SVG](https://drive.google.com/file/d/1EcPtldZ570FAW30ckSY1XBvk_Lb1FDJL/view?usp=sharing) (use screen zoom for readable details).



<p id="gdcalert68" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image68.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert69">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image68.jpg "image_tooltip")


Image 4.1 - MITRE ATT&CK Navigator Map (page 1 of 3) - Reconnaissance to Persistence

Legend:



* Performed successfully
* Failure to perform



<p id="gdcalert69" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image69.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert70">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image69.jpg "image_tooltip")


Image 4.2 - MITRE ATT&CK Navigator Map (page 2 of 3) - Privilege Escalation to Discovery

Legend:



* Performed successfully
* Failure to perform



<p id="gdcalert70" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image70.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert71">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image70.jpg "image_tooltip")


Image 4.3 - MITRE ATT&CK Navigator Map (page 3 of 3) - Lateral Movement to Impact

Legend:



* Performed successfully
* Failure to perform
