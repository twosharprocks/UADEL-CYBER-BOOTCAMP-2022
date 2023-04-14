## **Vandalay Industries Monitoring Activity Instructions**


## **Step 1: The Need for Speed**

**Background**: As the worldwide leader of importing and exporting, Vandalay Industries has been the target of many adversaries attempting to disrupt their online business. Recently, Vandalay has been experiencing DDOS attacks against their web servers.

Not only were Vandalay web servers taken offline by a DDOS attack, but upload and download speed were also significantly impacted after the outage. Your networking team provided results of a network speed run around the time of the latest DDOS attack.

**Your Task**: Create a report to determine the impact of the DDOS attack on upload and download speed. Create an additional field to calculate the ratio of the upload speed to the download speed. To do so, complete the following steps:



1. Upload the following file containing the system speeds around the time of the attack:
    * [Speed Test File](https://drive.google.com/file/d/1sAIEh_vxhjJJpj3NiPx8Wele_-cfEZTK/view?usp=sharing)
2. Using the `eval` command, create a field called `ratio` that shows the ratio between the upload and download speeds.

3. Create a report using Splunk's `table` command to display the following fields in a statistics report: 
    * `_time`
    * `IP_ADDRESS`
    * `DOWNLOAD_MEGABITS`
    * `UPLOAD_MEGABITS`
    * `ratio`

`eval ratio='UPLOAD_MEGABITS' / 'DOWNLOAD_MEGABITS' | table _time IP_ADDRESS DOWNLOAD_MEGABITS UPLOAD_MEGABITS ratio`

4. Answer the following questions in the M19 Submission File:
    * **(1)** Based on the report you created, what is the approximate date and time of the attack? `At approximately 14:30 on 2020-02-23`
    * **(2)** How long did it take your systems to recover? `Full recovery took ~9 hours (recovery by approx 23:30 on 2020-02-23)`
5. Make sure to include a screenshot of your report along with the answers to these questions.

[Screenshot](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module19_SIEMS/Mod19-im1.jpg)

### **Step 2: Are We Vulnerable?**

**Background:** Due to the frequency of attacks, your manager needs to be sure that sensitive customer data on their servers is not vulnerable. Since Vandalay uses Nessus vulnerability scanners, you have pulled the last 24 hours of scans to see if there are any critical vulnerabilities.

**Your Task:** Create a report determining how many critical vulnerabilities exist on the customer data server. Then, build an alert to notify your team if a critical vulnerability reappears on this server. To do so, complete the following steps:



1. Upload the following file from the Nessus vulnerability scan:
    * [Nessus Scan Results](https://drive.google.com/file/d/1AonO8jAN4nKniZDw5qAYoMamBBXLpkdr/view?usp=sharing)
2. Create a report that shows the `count` of critical vulnerabilities from the customer database server. `severity=critical dest_ip="10.11.36.23"`
    * The database server IP is `10.11.36.23`.
    * The field that identifies the level of vulnerabilities is `severity`.
3. Build an alert that monitors every day to see if this server has any critical vulnerabilities. If a vulnerability exists, have an alert emailed to `soc@vandalay.com`.
4. In your M19 Submission File, include a screenshot of your report and a screenshot showing that the alert has been created.

[Screenshot](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module19_SIEMS/Mod19-im2-1.jpg)

[Screenshot](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module19_SIEMS/Mod19-im2-2.jpg)

### **Step 3: Drawing the (Base)line**

**Background**: A Vandaly server is also experiencing brute force attacks into their administrator account. Management would like you to set up monitoring to notify the SOC team if a brute force attack occurs again.

**Your Task**: Analyze administrator logs that document a brute force attack. Then, create a baseline of the ordinary amount of administrator bad logins and determine a threshold to indicate if a brute force attack is occurring. To do so, complete the following steps:



1. Upload the following administrator login logs:
    * [Admin Logins](https://drive.google.com/file/d/1q5OJzVpvW0ExKuc8BtQ2LQOqpneLpUUy/view?usp=sharing)
2. Answer the following in the M19 Submission File:
    * **(1)** When did the brute force attack occur? `Between 09:00 and 14:00 on 2020-02-21`
    * **(2)** Determine a baseline of normal activity and a threshold that would alert if a brute force attack is occurring. `Baseline = 15 failed logins per hour. Alert threshold set at 30 failed logins per hour.`
    * **(3)** Design an alert to check the threshold every hour and email the SOC team at SOC@vandalay.com if triggered. Provide a screenshot showing that the alert has been created.
   
   [Screenshot](https://github.com/twosharprocks/UADEL-CYBER-BOOTCAMP-2022/blob/main/Homework/Module19_SIEMS/Mod19-im3.jpg)