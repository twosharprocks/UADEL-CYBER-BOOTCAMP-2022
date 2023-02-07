## Activity File: Security Onion and NSM

In this activity, you will continue your role as an SOC Analyst for the California DMV. 

- You’ve implemented a new security control as part of your network security monitoring (NSM) program.

- Your NSM program will help your organization understand the limits of what it can detect, adversarial tactics, and how to quickly apply lessons learned to mitigate newly discovered security vulnerabilities.

- Your CISO has advocated for using Security Onion as your open source NSM system to detect and analyze all intrusion attempts. 

- Your CISO provided the following questions to help you test your knowledge of Security Onion and NSM before launching the new system. 

### Instructions

Complete the following:

1. Click the Sguil desktop icon and launch the application.

2. Log in using the same credentials.

  - When prompted, select **both** networks to monitor. 
  
3. Pick one alert and answer the following questions:

    - What is the alert status? `Red`
    - What are the source and destination IP addresses? `Source: 192.168.3.35 Destination: 195.2.253.92`
    - What are the source and destination ports? `Source: 1032 Destination: 80`
    - In the IP resolution section, perform a reverse DNS lookup of the attacker. What information is revealed? `IPv4 address block not managed by the RIPE NCC`
    - What is the alert ID for the alert you chose? `3.1`

4. Define the Snort rule that triggers the alert you chose:

    - Action `alert`
    - Protocol `tcp`
    - Source IP `192.168.3.35`
    - Source port `1032`
    - Direction `->`
    - Destination IP `195.2.253.92`
    - Destination port `80`
    - Message `GET /tdfpmmn/hnkppz.php?adv=516 HTTP/1.1..User-Agent:Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1) ver49..Host:acxerox.com....`

#### Bonus Questions

Answer the following questions as true or false:

1. NSM is vulnerability-centric, with its primary focus on the vulnerability and not the adversary. `True`


2. The strength of NSM is its focus on the visibility of an attack, not its control. `True`


3. NSM can see inside encrypted traffic. `False`


4. Alerts in Security Onion's Sguil console are the equivalent of an Indicator of Attack, or IOA. `True`


5. NSM allows organizations to track and uncover malware. `True`


6. The Snort IDS engine drives the functionality of the Sguil analyst's console. `True`


Answer the following questions:

1. Name two methods for physically connecting an IDS to a network. `TAP` and `SPAN`


2. Name the two stages of NSM and their processes. `Detection` and `Response`

