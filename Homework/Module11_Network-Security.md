## Network Security Homework

----

## Part 1: Review Questions

#### Security Control Types

With the understanding that Defense in Depth can be broken down into three different security control types, answer the following questions:

1. Walls, bollards, fences, guard dogs, cameras, and lighting are what type of security control?

   > `Physical`

2. Security awareness programs, BYOD policies, and ethical hiring practices are what type of security control?

   > `Administrative`

3. Encryption, biometric fingerprint readers, firewalls, endpoint security, and intrusion detection systems are what type of security control?

   > `Technical`

#### Intrusion Detection and Attack indicators

1. What's the difference between an IDS and an IPS?

   > `An IDS only monitors and logs network traffic without modifying it, whereas an IPS monitors, logs and can modify/block traffic if a threat is detected.`

2. What's the difference between an Indicator of Attack and an Indicator of Compromise?

   > `An IOA is an indicator that an attack is happening right now or very recently, while an IOC is an indicator that occured in the past`

#### The Cyber Kill Chain

Name each of the seven stages for the Cyber Kill chain and provide a brief example of each.

1. `Reconnaissance - Harvesting OSINT, email addresses, DNS records, ect`

2. `Weaponisation - Establish an attack vector such as a vulnerability and develop a payload`

3. `Delivery - BadUSB, Malicious Email, SQL injection`

4. `Exploitation - Activation of vulnerability, clicking malicious email link`

5. `Installation - Web server shell or backdoor, add OS services for persistence`

6. `Command & Control (C2) - Web, DNS, Email to establish two-way communications`

7. `Actions on Objectives - Collect/modify/destroy data and user credentials`


#### Snort Rule Analysis

Use the Snort rule to answer the following questions:

Snort Rule #1

```bash
alert tcp $EXTERNAL_NET any -> $HOME_NET 5800:5820 (msg:"ET SCAN Potential VNC Scan 5800-5820"; flags:S,12; threshold: type both, track by_src, count 5, seconds 60; reference:url,doc.emergingthreats.net/2002910; classtype:attempted-recon; sid:2002910; rev:5; metadata:created_at 2010_07_30, updated_at 2010_07_30;)
```

1. Break down the Sort Rule header and explain what is happening.

   > `Generates an alert for any inbound tcp traffic from anywhere and from any port heading to $HOME_NET on port 5800 to 5820`

2. What stage of the Cyber Kill Chain does this alert violate?

   > `Stage 2 - Reconnaissance`

3. What kind of attack is indicated?

   > `Potential VNC Scan 5800-5820 (Port Scanning)`

Snort Rule #2

```bash
alert tcp $EXTERNAL_NET $HTTP_PORTS -> $HOME_NET any (msg:"ET POLICY PE EXE or DLL Windows file download HTTP"; flow:established,to_client; flowbits:isnotset,ET.http.binary; flowbits:isnotset,ET.INFO.WindowsUpdate; file_data; content:"MZ"; within:2; byte_jump:4,58,relative,little; content:"PE|00 00|"; distance:-64; within:4; flowbits:set,ET.http.binary; metadata: former_category POLICY; reference:url,doc.emergingthreats.net/bin/view/Main/2018959; classtype:policy-violation; sid:2018959; rev:4; metadata:created_at 2014_08_19, updated_at 2017_02_01;)
```

1. Break down the Sort Rule header and explain what is happening.

   > `Generates an alert for any inbound tcp traffic from anywhere and on port 80, heading to $HOME_NET on any port`

2. What stage of the Cyber Kill Chain does the alerted activity violate?

   > `Stage 3 - Delivery`

3. What kind of attack is this rule monitoring?

   > `Emerging threat - Policy violation by EXE or DLL Windows file download by HTTP`

Snort Rule #3

- Your turn! Write a Snort rule that alerts when traffic is detected inbound on port 4444 to the local network on any port. Be sure to include the `msg` in the Rule Option.

   > `alert tcp $EXTERNAL_NET 4444 -> $HOME_NET any (msg:"ET POLICY TROJAN Possible W32.Blaster.Worm")`


### Part 2: "Drop Zone" Lab

#### Log into the Azure `firewalld` machine

Log in using the following credentials:

- Username: `sysadmin`
- Password: `cybersecurity`
    
#### Uninstall `ufw`

Before you get started, it's generally best practice to ensure that you do not have any instances of `ufw` running in order to avoid conflicts with your `firewalld` service. Additionally, this ensures that `firewalld` will be your default firewall.

- Run the command that removes any running instance of `ufw`.

    `sudo apt remove ufw`

#### Enable and start `firewalld`

By default, these service should be running. If not, then run the following commands:

- Run the commands that enable and start `firewalld` upon boots and reboots.

    `sudo systemctl enable firewalld`
    `sudo systemctl start firewalld`

  Note: This will ensure that `firewalld` remains active after each reboot.
    
#### Confirm that the service is running.

- Run the command that checks whether or not the `firewalld` service is up and running.

    `sudo systemctl status firewalld`
    
    
#### List all firewall rules currently configured.

Next, lists all currently configured firewall rules. This will give you a good idea of what's currently configured and save you time in the long run by not doing double work.

- Run the command that lists all currently configured firewall rules:

    `sudo firewall-cmd --list-all`

- Take note of what Zones and settings are configured. You many need to remove unneeded services and settings. 

#### List all supported service types that can be enabled.

- Run the command that lists all currently supported services to see if the service you need is available

    `sudo firewall-cmd --get-services`

 Note: that we can see that the `Home` and `Drop` Zones are created by default.
    
#### Zone Views

- Run the command that lists all currently configured zones.

    `sudo firewall-cmd --list-all-zones`

- We can see that the `Public` and `Drop` Zones are created by default. Therefore, we will need to create Zones for `Web`, `Sales`, and `Mail`.

#### Create Zones for `Web`, `Sales` and `Mail`.

- Run the command that creates Web, Sales and Mail zones.

    `$ sudo firewall-cmd --permanent --new-zone=web`
    `$ sudo firewall-cmd --permanent --new-zone=sales`
    `$ sudo firewall-cmd --permanent --new-zone=mail`

- Reload the firewalld service in order to apply your changes. 
  - Run: `firewall-cmd --reload` or `systemctl restart firewalld` .

#### Set the zones to their designated interfaces:

- Run the command that sets your `eth` interface to your zones.

    `$ sudo firewall-cmd --zone=public --change-interface=eth0`
    `$ sudo firewall-cmd --zone=web --change-interface=eth1`
    `$ sudo firewall-cmd --zone=sales --change-interface=eth2`
    `$ sudo firewall-cmd --zone=mail --change-interface=eth3`

#### Add services to the active zones:

- Run the commands that add services to the **public** zone, the **Web** zone, the **sales** zone,and the **mail** zone.

- Public:

    `$ sudo firewall-cmd --zone=public --add-service=http`
    `$ sudo firewall-cmd --zone=public --add-service=https`
    `$ sudo firewall-cmd --zone=public --add-service=smtp`
    `$ sudo firewall-cmd --zone=public --add-service=pop3`

- Web: 

    `$ sudo firewall-cmd ???-permanent ???-zone=web ???-add-service=http`

- Sales

    `$ sudo firewall-cmd ???-permanent ???-zone=sales ???-add-service=https`

- Mail

    `$ sudo firewall-cmd ???-permanent ???-zone=mail ???-add-service=smtp`
    `$ sudo firewall-cmd ???-permanent ???-zone=mail ???-add-service=pop3`


- What is the status of `http`, `https`, `smtp` and `pop3`?

   `sudo firewall-cmd --list-services`
   `Active services = dhcpv6-client http https pop3 smtp ssh`


#### Add you adversaries to the Drop Zone.

- Run the command that will add all current and any future blacklisted IPs to the Drop Zone.

     `$ sudo firewall-cmd --permanent --zone=drop --add-source=10.208.56.23`
     `$ sudo firewall-cmd --permanent --zone=drop --add-source=135.95.103.76`
     `$ sudo firewall-cmd --permanent --zone=drop --add-source=76.34.169.118`
    
#### Make rules permanent then reload them:

It's good practice to ensure that your `firewalld` installation remains nailed up and services across reboots. This ensure that the network remains secured after unplanned outages such as, power failures.

- Run the command that reloads the `firewalld` configurations and writes it to memory

    `$ sudo firewall-cmd --reload`
 
#### View active Zones

Now we'll want to provide truncated listings of all currently active zones. This a good point to verify your zone settings.

- Run the command that displays all zone services.

    `$ sudo firewall-cmd --get-active-zones`

#### Block an IP address

- Use a rich-rule that blocks the IP address `138.138.0.3`.

    `$ sudo firewall-cmd --zone-public --add-rich-rule=???rule family=???ipv4??? source address=???138.138.0.3??? reject???`

#### Block Ping/ICMP Requests

You've decided to harden your network against `ping` scans by blocking `icmp ehco` replies.

- Run the command that blocks `pings` and `icmp` requests in your `public` zone.

    `    $ sudo firewall-cmd --zone=public --add-icmp-block=echo-reply --add-icmp-block=echo-request`

#### Rule Check

Now that you've set up your brand new `firewalld` installation, it's time to verify that all of the settings have taken effect.

- Run the command that lists all  of the rule settings. Do one command at a time for each zone.

    `$ sudo firewall-cmd --zone=public --list-all`
    `$ sudo firewall-cmd --zone=web --list-all`
    `$ sudo firewall-cmd --zone=sales --list-all`
    `$ sudo firewall-cmd --zone=mail --list-all`
    `$ sudo firewall-cmd --permanent --zone=drop --list-all`

- Are all of our rules are in place? If not, then go back and make the necessary modification before checking again.

---


### Part 3: IDS, IPS, DiD and Firewalls

#### IDS vs. IPS Systems

1. Name and define two ways an IDS connects to a network.

   > `Network Test Access Port (TAP) - A physical hardware device that makes copies of both send and receive traffic while still allowing network traffic through uninterrupted`

   > `Port Mirroring (SPAN Port) - Mirrors all packet to another port to be captured & analysed.`

2. Describe how an IPS connects to a network.

   > `Inline with the flow of data, generally between the firewall and network switch`

3. What type of IDS compares patterns of traffic to predefined signatures and is unable to detect Zero-Day attacks?

   > `Signature-based`

4. Which type of IDS is beneficial for detecting all suspicious traffic that deviates from the well-known baseline and is excellent at detecting when an attacker probes or sweeps a network?

   > `Anomaly-based`

#### Defense in Depth

- For each of the following scenarios, provide the layer of Defense in Depth that applies:

1.  A criminal hacker tailgates an employee through an exterior door into a secured facility, explaining that they forgot their badge at home. 

    > `Physical`

2. A zero-day goes undetected by antivirus software.

    > `Technical-Application`

3. A criminal successfully gains access to HR???s database.

    > `Technical-Data`

4. A criminal hacker exploits a vulnerability within an operating system.

    > `Technical-Host`

5. A hacktivist organization successfully performs a DDoS attack, taking down a government website.

    > `Technical-Network`

6. Data is classified at the wrong classification level.

    > `Administration-Policies, Procedures & Awareness`

7. A state sponsored hacker group successfully firewalked an organization to produce a list of active services on an email server.
    
    > `Technical-Perimeter`

- Name one method of protecting data-at-rest from being readable on hard drive.

    > `Encryption`

- Name one method to protect data-in-transit.

    > `VPN`

- What technology could provide law enforcement with the ability to track and recover a stolen laptop.

   > `GPS & GSM Tracking`

- How could you prevent an attacker from booting a stolen laptop using an external hard drive?

    > `Set a firmware password`

#### Firewall Architectures and Methodologies

1. Which type of firewall verifies the three-way TCP handshake? TCP handshake checks are designed to ensure that session packets are from legitimate sources.

   > `Circuit-level Gateway`

2. Which type of firewall considers the connection as a whole? Meaning, instead of looking at only individual packets, these firewalls look at whole streams of packets at one time.

   > `Stateful Packet Filtering`

3. Which type of firewall intercepts all traffic prior to being forwarded to its final destination. In a sense, these firewalls act on behalf of the recipient by ensuring the traffic is safe prior to forwarding it?

   > `Application`

4. Which type of firewall examines data within a packet as it progresses through a network interface by examining source and destination IP address, port number, and packet type- all without opening the packet to inspect its contents?

   > `Stateless`


5. Which type of firewall filters based solely on source and destination MAC address?

   > `MAC Layer`


----

### Bonus Lab: "Green Eggs & SPAM"

Locate the indicator of attack in Sguil based off of the following:

Source IP/port: 188.124.9.56:80
Destination address/port: 192.168.3.35:1035
Event message: ET TROJAN JS/Nemucod.M.gen downloading EXE payload

Answer the following questions:

1. What was the indicator of an attack? (Hint: What do the details reveal?)
   `Sguil Red alert identifying download of EXE payload for JS-Nemucod Trojan`
   
2. What was the adversarial motivation (purpose of the attack)?
   ` Financial (Info-stealing & Ransomware)`
   
3. Describe observations and indicators that may be related to the perpetrators of the intrusion. Categorize your insights according to the appropriate stage of the cyber kill chain, as structured in the following table:
   
* Reconnaissance    `Listed Email addresses`
* Weaponization     `Neumcod Javascript downloader`
* Delivery          `Zip file attached to spam email`
* Exploitation      `Installs further malware`
* Installation      `Javascript downloads executable, installs and runs through ActiveX control, before opening a dummy PDF to mislead the user`
* Command & Control `Trojan contacts remote host davis1.ru through port 80`
* Actions on Obj.   `Downloads and executes ransomware such as TeslaKey or Locky`

4. What are your recommended mitigation strategies?
   `Regular cybersecurity awareness training to reinforce spam identification and not opening unverified attachments`
  
5. List your third-party references.
* https://www.certego.net/en/news/italian-spam-campaigns-using-js-nemucod-downloader/
* https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?Name=TrojanDownloader:JS/Nemucod
* https://blogs.blackberry.com/en/2018/12/cylance-vs-nemucod-trojan-downloader
