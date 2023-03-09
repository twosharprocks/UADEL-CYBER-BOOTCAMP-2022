## Testing Web Applications for Vulnerabilities

Make a copy of this document to work in, and then respond to each question below the prompt. Save and submit this completed file as your Challenge deliverable.


### Web Application 1: _Your Wish is My Command Injection_

Provide a screenshot confirming that you successfully completed this exploit:

![hosts](https://raw.githubusercontent.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/main/Homework/Module15_Web-Vuln/webapp1-hosts.jpg)
![passwd](https://raw.githubusercontent.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/main/Homework/Module15_Web-Vuln/webapp1-passwd.jpg)

Write two or three sentences outlining mitigation strategies for this vulnerability: 


`Whitelist allowed characters such as a-z, 0-9
Provide users, applications and processes with least privilege
Update/Patch systems to remove vulnerability`



### Web Application 2: _A Brute Force to Be Reckoned With_

Provide a screenshot confirming that you successfully completed this exploit:

![Ironman](https://raw.githubusercontent.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/main/Homework/Module15_Web-Vuln/webapp2-burp.jpg)

Write two or three sentences outlining mitigation strategies for this vulnerability: 


`Increase password complexity to increase length and include capitals, numbers and other characters. 
Rate-limit login attempts
Force users to change passwords after a known breach`



### Web Application 3: _Where's the BeEF?_

Provide a screenshot confirming that you successfully completed this exploit:

![Beefus](https://raw.githubusercontent.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/main/Homework/Module15_Web-Vuln/webapp3%20-%20beef%20exploit1.jpg)
![ChromeUpdate](https://raw.githubusercontent.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/main/Homework/Module15_Web-Vuln/webapp3%20-%20beef%20chromeupdate.jpg)
![Facebook Login](https://raw.githubusercontent.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/main/Homework/Module15_Web-Vuln/webapp3%20-%20beef%20facebook.jpg)
![Geo Location](https://raw.githubusercontent.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/main/Homework/Module15_Web-Vuln/webapp3%20-%20beef%20geo.jpg)

Write two or three sentences outlining mitigation strategies for this vulnerability: 

* `Validate input to block &lt;script> tags (and capitalisation variations)`
* `Encode JAVA output`
* `Sanitise HTML output (if page is static)`
