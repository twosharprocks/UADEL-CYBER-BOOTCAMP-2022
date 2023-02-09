## Activity File: Alert - C2 Beacon

In this activity, you will continue your role as an SOC analyst for the California Department of Motor Vehicles (DMV).

- Your organization has just experienced another, more sophisticated attack. It’s a red alert that Snort has identified as an emerging threat: a C2 beacon acknowledgement attack.

- The entire network is down across the state. As long as the network is down, none of the DMV offices can issue or renew licenses and registrations, or complete driving tests.

- As part of the Computer Incident and Response Team (CIRT), you need to establish an attacker profile that includes the tactics, techniques, and procedures used by the adversary, and document all of your findings. Like a real security analyst, you may need to research other sources to answer all the questions.  

### Instructions

Use the following indicator of attack:

- Source IP: Attacker `67.183.123.151`

- Destination IP: Victim  `192.168.204.137`

- Snort Message: `ET TROJAN W32/Asprox.ClickFraudBot CnC Beacon Acknowledgment`

**Note:** You'll notice many attacks targeting the victim IP address. Please make sure to focus on the `ET TROJAN W32/Asprox.ClickFraudBot CnC Beacon Acknowledgment` attack.


Open Sguil and filter the source IP `67.183.123.151`

1. What Snort rule triggered this alert? `alert tcp $EXTERNAL_NET $HTTTP_PORTS -> $HOME_NET any (msg:"ET TROJAN W32/Asprox.ClickFraudBot CnC Beacon Acknowledgement"


2. According to the Snort rule, what is the destination port? `49159`


3. Taking a closer look at the Snort rule option, what is the message in the HTML body of the Content section? `hi!`


From the Sguil console, right-click on the Alert ID and pivot to Transcript, then scroll to the bottom of the Transcript window.  

4. What is the message in the HTML body? `hi!`

Close the Transcript window and go back to the Snort rule window. Click on the research.zscaler.com URL. A web browser will launch and take you to the Zscaler website. Read through the article and then answer the remaining questions.  

 (If the link is down, use this link instead to answer the following questions: [New Asprox Variant Goes Above And Beyond To Hijack Victims](https://www.zscaler.com/blogs/research/new-asprox-variant-goes-above-and-beyond-hijack-victims).)

5. What type of threat is this? `Command and Control`


6. Did this threat remove Windows registry keys? `No - it disables them`


7. Why does this threat disable key Windows processes? `Hinder removal`


9. What does CnC stand for and what is it? `Command and Control`


10. What is the term to describe a computer that's under the control of a C2 server? `Zombie`

#### Bonus Questions


11. Name one of the most popular techniques an adversary uses to infect a host with a botnet. `Code Injection`


12. What are two ways an organization can mitigate this type of a threat? `Anti-virus/HIDS, IDS/IPS`


13. How far up the cyber kill chain did this attack get? `Phase 6 - Command and Control`


14. What procedure does this threat use to hide when it's discovered? `Deletes itself`


15. Why is this threat persistent? `Creates entry in security center to keep creating itself`


16. What message does the victim's computer send to the CnC to let it know that it's alive, listening, and waiting? `GET`


17. What tactic does this threat use to remain hidden and unnoticed? `creates random file names`
