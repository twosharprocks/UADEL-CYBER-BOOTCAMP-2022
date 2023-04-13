## Activity File: Splunk Warm Up 

In today's activities, you will continue to play the role of the SOC manager at Omni Medical Products (OMP).

- Your Networking team noted suspicious activity and pulled logs from their Fortinet IPS system for you to investigate.

- You are tasked with analyzing the logs, determining the issue, and offering any mitigation strategies.


### Instructions

1. Upload the provided log file: `fortinet_IPS_logs.csv`

2. Determine the top source IP address. `41.146.8.66`

3. Determine the primary attack name in the logs. `Oracle.9i.TNS.OneByte.DoS`

4. Answer the following questions. (Use Google to assist in your research.)

    - Fortinet logs are from which type of device? `Firewall`

    - What is the city and country of the top source IP address? `Phoenix - South Africa`

    - Provide a brief summary of the attack name found. `Vulnerability in Oracle that allows an attacker to craft a single byte packet that crashes the TNS listener to cause a Denial-of-Service`
    
    - What is a recommended mitigation for this attack? `Patch software (vulnerability fixed by Oracle in 2005) and use defense-in-depth`

---
