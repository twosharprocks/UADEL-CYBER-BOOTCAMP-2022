# MegaCorpOne - Penetration Test Report - Two Sharp Rocks, LLC

## Confidentiality Statement

This document contains confidential and privileged information from MegaCorpOne Inc. (henceforth known as MegaCorpOne). The information contained in this document is confidential and may constitute inside or non-public information under international, federal, or state laws. Unauthorized forwarding, printing, copying, distribution, or use of such information is strictly prohibited and may be unlawful. If you are not the intended recipient, be aware that any disclosure, copying, or distribution of this document or its parts is prohibited.

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
  <tr>
   <td><strong>Contact Phone</strong>
   </td>
   <td>(+61) 480 080 934
   </td>
  </tr>
  <tr>
   <td><strong>Contact Email</strong>
   </td>
   <td>josh@joshrichards.com.au
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
   <td>29/03/2023
   </td>
   <td>Josh Richards
   </td>
   <td>Initial Report
   </td>
  </tr>
</table>



# 


## Introduction

In accordance with MegaCorpOne’s policies, Two Shark Rocks, LLC (henceforth known as TSR) conducts external and internal penetration tests of its networks and systems throughout the year. The purpose of this engagement was to assess the networks’ and systems’ security and identify potential security flaws by utilizing industry-accepted testing methodology and best practices. The project was conducted on a number of systems on MegaCorpOne’s network segments by TSR during March of 2023.

For the testing, TSR focused on the following:



* Attempting to determine what system-level vulnerabilities could be discovered and exploited with no prior knowledge of the environment or notification to administrators.
* Attempting to exploit vulnerabilities found and access confidential information that may be stored on systems.
* Documenting and reporting on all findings.

All tests took into consideration the actual business processes implemented by the systems and their potential threats; therefore, the results of this assessment reflect a realistic picture of the actual exposure levels to online hackers. This document contains the results of that assessment.


### Assessment Objective

The primary goal of this assessment was to provide an analysis of security flaws present in MegaCorpOne’s web applications, networks, and systems. This assessment was conducted to identify exploitable vulnerabilities and provide actionable recommendations on how to remediate the vulnerabilities to provide a greater level of security for the environment.

TSR used its proven vulnerability testing methodology to assess all relevant web applications, networks, and systems in scope. 

MegaCorpOne has outlined the following objectives:

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
   <td>Escalate privileges to domain administrator.
   </td>
  </tr>
  <tr>
   <td>Compromise at least two machines.
   </td>
  </tr>
</table>


## Penetration Testing Methodology


### Reconnaissance 

TSR begins assessments by checking for any passive (open source) data that may assist the assessors with their tasks. If internal, the assessment team will perform active recon using tools such as Nmap and Bloodhound.


### Identification of Vulnerabilities and Services

TSR uses custom, private, and public tools such as Metasploit, hashcat, and Nmap to gain perspective of the network security from a hacker’s point of view. These methods provide MegaCorpOne with an understanding of the risks that threaten its information, and also the strengths and weaknesses of the current controls protecting those systems. The results were achieved by mapping the network architecture, identifying hosts and services, enumerating network and system-level vulnerabilities, attempting to discover unexpected hosts within the environment, and eliminating false positives that might have arisen from scanning. 


### Vulnerability Exploitation

TSR’s normal process is to both manually test each identified vulnerability and use automated tools to exploit these issues. Exploitation of a vulnerability is defined as any action we perform that gives us unauthorized access to the system or the sensitive data. 


### Reporting

Once exploitation is completed and the assessors have completed their objectives, or have done everything possible within the allotted time, the assessment team writes the report, which is the final deliverable to the customer.

## Scope

Prior to any assessment activities, MegaCorpOne and the assessment team will identify targeted systems with a defined range or list of network IP addresses. The assessment team will work directly with the MegaCorpOne POC to determine which network ranges are in-scope for the scheduled assessment. 

It is MegaCorpOne’s responsibility to ensure that IP addresses identified as in-scope are actually controlled by MegaCorpOne and are hosted in MegaCorpOne-owned facilities (i.e., are not hosted by an external organization). In-scope and excluded IP addresses and ranges are listed below. 


<table>
  <tr>
   <td><strong>IP Address/URL</strong>
   </td>
   <td><strong>Description</strong>
   </td>
  </tr>
  <tr>
   <td>172.22.117.0/16
<p>
MCO.local
<br>
*.Megacorpone.com
   </td>
   <td>MegaCorpOne internal domain, range and public website
   </td>
  </tr>
</table>


## Executive Summary of Findings


### Grading Methodology

Each finding was classified according to its severity, reflecting the risk each such vulnerability may pose to the business processes implemented by the application, based on the following criteria:

**Critical**:	 Immediate threat to key business processes.

**High**:		 Indirect threat to key business processes/threat to secondary business processes.

**Medium**:	 Indirect or partial threat to business processes. 

**Low**:		 No direct threat exists; vulnerability may be leveraged with other vulnerabilities.

Informational:    No threat; however, it is data that may be used in a future attack.

As the following grid shows, each threat is assessed in terms of both its potential impact on the business and the likelihood of exploitation:

![risk-matrix](
<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")



### Summary of Strengths

While the assessment team was successful in finding several vulnerabilities, the team also recognized several strengths within MegaCorpOne’s environment. These positives highlight the effective countermeasures and defenses that successfully prevented, detected, or denied an attack technique or tactic from occurring. 



* Domain Controllers restricted to Network Administrator
* Passwords managed and stored as hashes 


### Summary of Weaknesses

TSR successfully found several critical vulnerabilities that should be immediately addressed in order to prevent an adversary from compromising the network. These findings are not specific to a software version but are more general and systemic vulnerabilities.



* Common use of weak passwords and password reuse by both administrators and users
* Administrator and user credentials shared in clear text files
* Unpatched software on critical network infrastructure
* System processes not protected from cache and credential dumping

## Executive Summary

Initial reconnaissance of megacorpone.com using recon-ng provided a list of active sub-domains and their ip addresses (T1595: Active Scanning). 



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.jpg "image_tooltip")


Image 1.1 - Recon-ng results for megacorpone.com (vpn.megacorpone.com highlighted in red)

From this list, **vpn.megacorpone.com** was identified as a strong candidate for initial access. Potential employee usernames had been collected through OSINT (T1589.003: Employee Names) and simple password guessing was attempted on the vpn.megacorpone.com login prompt (T1078: Valid Accounts).



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.jpg "image_tooltip")


Image 1.2 - Attempting login through vpn.megacorpone.com (user ‘thudson’ password ‘thudson’)



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.jpg "image_tooltip")


Image 1.3 - Successful login to vpn.megacorpone.com with ‘thudson:thudson’ 

Initial access was initially achieved through successfully guessing user ‘thudson’ was using weak password ‘thudson’ (T1110.001: Password Guessing). Access to vpn.megacorpone.com listed three files (Image 1.3), including a password list (password.lst) and a script (vpn.sh). Inspection of vpn.sh provided usernames and passwords to four additional users (T1087: Account Discovery).



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image5.jpg "image_tooltip")


Image 1.4 - Contents of vpn.sh showing usernames & passwords

Running Nmap and ZenMap against 172.22.117.100/16, two hosts (T1018: Remote System Discovery) were identified:



* 172.22.117.100 (Kali Linux - penetration tester’s machine)
* 172.22.117.150 (Metasploitable - Linux 2.6.9 machine, potential domain server)

Port scanning 172.22.117.150 revealed numerous open ports, the system OS, and an exploitable vulnerability in vsftpd 2.3.4 on port 21 (T1082: System Information Discovery).



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image6.jpg "image_tooltip")


Image 2.1 - Zenmap scan against 172.22.117.150 with system name, OS, and vsftpd 2.3.4 backdoor

Executing the vsftpd 2.3.4 backdoor exploit (aka “49757.py”) against 172.22.117.150 provides shell access as the root user (T1059: Command and Scripting Interpreter), and allows for the display of password hashes for the machine’s users (T1033: System Owner/User Discovery).



<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image7.jpg "image_tooltip")


Image 2.2 - Exploitation of vsftpd 2.3.4 backdoor for root access & password hashes 

Cracking the password hashes in John the Ripper (T1110.002: Password Cracking) with the passwords.lst wordlist from vpn.megacorpone.com produced the passwords for seven users.



<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image8.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image8.jpg "image_tooltip")


Image 2.3 - Passwords for sys, klog, msfadmin, postgres, user, service, and tstark.

Knowing “metasploitable” operates on a linux OS, the distcc_exec exploit was tested and proven to provide low-level system daemon access to 172.22.117.150 by binding it to the penetration tester’s host through a reverse shell (T1210: Exploitation of Remote Services).



<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image9.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image9.jpg "image_tooltip")


Image 3.1 - Using distcc_exec exploit to gain system daemon access to 172.22.117.150

This low-level daemon access was leveraged to locate and view numerous usernames and passwords stored in plain-text on the host (T1552.001: Credentials in Files), including the admin credentials for 172.22.117.150 which were previously cracked from hashes.



<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image10.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image10.jpg "image_tooltip")


Image 3.2 - Locating .txt files which include “password” in the name 

and displaying the contents of “adminpassword.txt”



It was then possible to login to 172.22.117.150 with administrator rights using the “msfadmin:cybersecurity” credentials (T1078.003: Local Accounts).



<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image11.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert12">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image11.jpg "image_tooltip")


Image 3.3 - Logging into 172.22.117.150 using administrator credentials

This administrator login allowed modification to the sshd_config file and open port 10022 for SSH (T1021.004), and the addition of user “systemd-ssh” (T1136: Create Account) in order to establish backdoor access and provide greater persistence in the system should defensive action be taken to secure 172.22.117.150.



<p id="gdcalert12" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image12.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert13">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image12.jpg "image_tooltip")


Image 4.1 - Display of users on 172.22.117.150 including new user “systemd-ssh”, 

followed by user’s elevation to sudo-ers group, and modification of sshd_config.



<p id="gdcalert13" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image13.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert14">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image13.jpg "image_tooltip")


Image 4.2 - Modification of sshd_config to open port 10022 to support persistent access



Having compromised the Linux host at 172.22.117.100, an Nmap scan was performed on a second network to identify Windows hosts (T1595: Active Scanning).



<p id="gdcalert14" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image14.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert15">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image14.jpg "image_tooltip")


Image 5.1 - Nmap scan of 172.22.117.100/24 showing two Windows hosts (172.22.117.10 & .20)

Using the nmap results we identified two Windows hosts with a range of open ports:



* 172.22.117.10 - Windows Domain Controller, with port 88 open for Kerberos
* 172.22.117.20 - Windows Host, with port 3390 open for Windows Terminal Services

To establish persistence, a reverse_tcp payload (shell.exe) was delivered via meterpreter to C:\ of the ‘tstark’ user on domain controller 172.22.117.10  (T1105: Ingress Tool Transfer). 



<p id="gdcalert15" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image15.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert16">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image15.jpg "image_tooltip")


Image 5.2 - Payload delivery via msfvenom, and login to tstark to show shell.exe in C:\

The command to execute the payload was performed via meterpreter by establishing an active session through the SMB Client, then delivering a wmiexec command to execute the shell.exe payload (T1059: Command and Scripting Interpreter).



<p id="gdcalert16" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image16.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert17">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image16.jpg "image_tooltip")


Image 5.3 - Establishing a meterpreter session to deliver the command to execute shell.com in C:\

To further establish persistence in the event shell.exe is identified and removed, meterpreter’s windows persistence service was also used to establish system process (LjUhES.exe) in tstark’s account that creates a reverse tcp session to the attacking machine (T1055.002: Portable Executable Injection). 



<p id="gdcalert17" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image17.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert18">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image17.jpg "image_tooltip")


Image 5.4 - Implanting a persistence service to maintain a reverse tcp process 

To protect this backdoor and maintain persistence, LjUhES.exe was added to the Windows Task Scheduler as “Backup” to run at midnight each night (T1053.005: Scheduled Task).



<p id="gdcalert18" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image18.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert19">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image18.jpg "image_tooltip")


Image 5.5 - Using a shell to 172.22.117.20 through ‘tstark’ to create a scheduled daily task that runs the implanted executable to re-establish the reverse TCP session

With a persistent backdoor established through the ‘tstark’ user, the kiwi module (aka Mimikatz) of meterpreter was then used to dump cached domain credentials (T1003.005: Cached Domain Credentials) from 172.22.117.20.



<p id="gdcalert19" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image19.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert20">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image19.jpg "image_tooltip")


Image 6.1 - Using Mimikatz to dump the LSA cache and reveal usernames & password hashes

Using John to once again to crack the retrieved hashes (T1110.002: Password Cracking), the passwords for bbanner and pparker were determined. Using the bbanner user credentials, lateral movement from 172.22.117.20 to the Domain Controller (172.22.117.10) was then successfully achieved through the use of the wmi exploit (T1210: Exploitation of Remote Services).



<p id="gdcalert20" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image20.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert21">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image20.jpg "image_tooltip")


Image 6.2 - Moving laterally from 172.22.117.20 to 172.22.117.10 and displaying system information

With administrator access to 172.22.117.10 (the Domain Controller) through a meterpreter session, a shell was created and the user accounts for the rest of the network were displayed.



<p id="gdcalert21" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image21.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert22">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image21.jpg "image_tooltip")


Image 6.3 - Shell creation and listing of network user accounts

With a list of usernames from the Domain Controller, it was then possible to use the kiwi module (Mimikatz) to perform a DCSync attack to dump each user’s credentials (T1003.006: DCSYnc).



<p id="gdcalert22" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image22.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert23">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image22.jpg "image_tooltip")


Image 6.4 - Dumping user password hashes from the Domain Controller


## Summary Vulnerability Overview


<table>
  <tr>
   <td><strong>Vulnerability</strong>
   </td>
   <td><strong>Severity</strong>
   </td>
  </tr>
  <tr>
   <td>Weak password on public web application
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Clear text password list stored on public web application
   </td>
   <td><strong>Medium</strong>
   </td>
  </tr>
  <tr>
   <td>Clear text user credentials stored on public web application
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Vulnerable software on network infrastructure
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Weak passwords on network infrastructure
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Clear text credentials stored on network infrastructure
   </td>
   <td><strong>Critical</strong>
   </td>
  </tr>
  <tr>
   <td>Unprotected system processes on Windows Systems
   </td>
   <td><strong>High</strong>
   </td>
  </tr>
  <tr>
   <td>Weak passwords on Windows Systems
   </td>
   <td><strong>High</strong>
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
   <td>3
   </td>
  </tr>
  <tr>
   <td>Ports
   </td>
   <td>1000
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
   <td>5
   </td>
  </tr>
  <tr>
   <td><strong>High</strong>
   </td>
   <td>2
   </td>
  </tr>
  <tr>
   <td><strong>Medium</strong>
   </td>
   <td>1
   </td>
  </tr>
  <tr>
   <td><strong>Low</strong>
   </td>
   <td>0
   </td>
  </tr>
</table>





## Vulnerability Findings


### Weak Password on Public Web Application

**Risk Rating**: **Critical**

**Description**: 

The site **vpn.megacorpone.com** is used to host the Cisco AnyConnect configuration file for MegaCorpOne. This site is secured with basic authentication but is susceptible to a dictionary attack. TSR was able to use a username gathered from OSINT in combination with a wordlist in order to guess the user’s password and access the configuration file.

**Affected Hosts**: vpn.megacorpone.com

**Remediation**: 



* Set up two-factor authentication instead of basic authentication to prevent dictionary attacks from being successful.
* Require a strong password complexity that requires passwords to be over 12 characters long, upper+lower case, & include a special character.
* Reset passwords for the following users: **thudson**, **trivera**, **msmith**, **mcarlow**,** **& **agrofield**


### Clear Text Password List Stored On Public Web Application

**Risk Rating**: **Medium**

**Description**: 

The site **vpn.megacorpone.com** is used to host a password.lst file which contains commonly used passwords as well as passwords used within MegaCorpOne. TSR was able to use this password list to considerably speed up the cracking of hashes for user passwords on both Linux and Windows systems.

**Affected Hosts**: vpn.megacorpone.com

**Remediation**: 



* Remove password.lst file from vpn.megacorpone.com to reduce the likelihood of dictionary attacks.


### Clear Text User Credentials Stored On Public Web Application

**Risk Rating**: **Critical**

**Description**: 

The site **vpn.megacorpone.com** is used to host a vpn.sh script file which contains clear text user credentials for MegaCorpOne employees. TSR was able to save these credentials for later use to impersonate users in other parts of the MegaCorpoOne network.

**Affected Hosts**: vpn.megacorpone.com

**Remediation**: 



* Remove vpn.sh file from vpn.megacorpone.com to prevent a breach of user credentials.
* Reset passwords for users: **thudson**, **trivera**, **msmith**, **mcarlow**,** **& **agrofield** 


### Vulnerable Software On Network Infrastructure

**Risk Rating**: **Critical**

**Description**: 

The domain server **metasploitable** (172.22.117.150) is running vsFTPd 2.3.4, an out-of-date version of FTP software which is vulnerable to a backdoor exploit (49757.py). TSR was able to use this exploit to gain root-level access to the system and exfiltrate user credentials.

**Affected Hosts**: 172.22.117.150

**Remediation**: 



* Update vsFTPd to the latest version (3.0.5 at time of writing).


### Weak Passwords on Network Infrastructure

**Risk Rating**: **Critical**

**Description**: 

The domain server **metasploitable** (172.22.117.150) has no requirement for strong user passwords. TSR was able to crack all user passwords on metasploitable in minutes using a widely-used password cracking tool.

**Affected Hosts**: 172.22.117.150

**Remediation**: 



* Require a strong password complexity that requires passwords to be over 12 characters long, upper+lower case, & include a special character.
* Reset passwords for users: **sys, klog, msfadmin, postgres, user, service, **& **tstark**


### Clear Text Credentials Stored on Network Infrastructure

**Risk Rating**: **Critical**

**Description**: 

The domain server **metasploitable** (172.22.117.150) has two text files (accounts.txt and adminpassword.txt) which contain clear text usernames and passwords for other network elements. TSR was able to use existing credentials to access and exfiltrate these user credentials for elevated network priveldge. 

**Affected Hosts**: 172.22.117.150

**Remediation**: 



* Remove all files which store user credentials in clear text.
* Reset password for Administration user **msfadmin**


### 


### Unprotected System Processes on Windows Systems

**Risk Rating**: **High**

**Description**: 

The Windows host (172.22.117.20) has unprotected system processes which are vulnerable to exploitation. TSR was able to migrate uploaded executables to more stable local system processes for greater persistence, and to dump local user credentials from LSA cache. 

**Affected Hosts**: 172.22.117.20

**Remediation**: 



* Enable protected mode (PPL) on LSASS to prevent LSA cache dumping
* Implement Windows Credential Guard


### Weak Passwords on Windows Systems

**Risk Rating**: **High**

**Description**: 

The Windows Host (172.22.117.20) and the Domain Controller (172.22.117.10) have no requirement for strong user passwords. TSR was able to crack all user passwords on both systems in minutes using a widely-used password cracking tool.

**Affected Hosts**: 172.22.117.20 and 172.117.10

**Remediation**: 

* Require a strong password complexity that requires passwords to be over 12 characters long, upper+lower case, & include a special character.
* Reset passwords for users: **bbanner, cdanvers, parker, sstrange,** **tstark** & **wmaximoff**




## MITRE ATT&CK Navigator Map

The following completed MITRE ATT&CK navigator map shows all of the techniques and tactics that TSR used throughout the assessment.


Legend:

* Yellow = Performed successfully
* Red = Failure to perform

A complete version of this MITRE ATT&CK Navigator Map is [available as a JSON](https://drive.google.com/file/d/1f-KErbE0lJpDWE19YCCo1FssO0vFJdrm/view?usp=sharing) or as a [standalone SVG](https://drive.google.com/file/d/13NXn8TY5XdXbM7pQLVlaEwfWPq4s50lR/view?usp=sharing).
