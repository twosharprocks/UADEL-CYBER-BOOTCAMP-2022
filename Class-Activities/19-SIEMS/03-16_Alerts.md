## Activity File: Scheduling Alerts 

- Now that you have determined the baselines, your manager would like you to monitor the Windows servers for brute force attacks.

- You are tasked with designing and scheduling an alert to notify your team if a brute force attack is occurring.

### Instructions

Using the thresholds produced from the last activity, design an alert with the following criteria:
  - Check if the threshold has been met every hour. `source="windowsrawlogs.txt" EventCode=4625` then `Save As`, `report`

  - If the threshold has been met, generate an email to SOC_Team@ompcompany.biz.

  - Title the alert message "Brute Force Alert" and provide the SOC instructions on how to proceed.
  
#### Bonus 

Another server is experiencing brute force attacks. However, this server has a much higher volume of activity.
- Upload and analyze the `bonus_logs.txt` file, then:

  - Determine when the attack occurred. `source="bonus_logs.txt" EventCode=4625` `5am-6am Web Feb 12`

  - Determine the baseline thresholds for alerts. 
  `| stats count by date_mday date_hour | stats median(count)` = 108
  `| stats count by date_mday date_hour | stats mean(count)` = 117.16
  `Set alert for 175 (eg. ~1.5x the mean)
  
  - Create an additional alert.
  `source="bonus_logs.txt" EventCode=4625`, `Save As --> Alert)`

---
