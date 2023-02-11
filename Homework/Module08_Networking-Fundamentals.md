## **Networking Fundamentals: Rocking your Network**

Make a copy of this document to work in, and then for each phase, add the solution below the prompt. Save and submit this completed file as your Challenge deliverable.


### Phase** 1: _“I’d like to Teach the World to <code>ping</code>”</em></strong>



1. Command(s) used to run `fping` against the IP ranges:

    * `fping -g 15.199.95.91/28`
    * `fping -g 15.199.94.91/28`
    * `fping -g 203.0.113.32/28`
    * `fping -g 161.35.96.20/32`
    * `fping -g 192.0.2.0/28`


2. Summarize the results of the `fping` command(s):

    * `15.199.95.91/28 - 15.199.95.81 to 15.199.95.94 are unreachable`
    * `15.199.94.91/28 - 15.199.94.81 to 15.199.94.94 are unreachable`
    * `203.0.113.32/28 - 203.0.113.81 to 203.0.113.94 are unreachable`
    * `161.35.96.20/32 - 161.35.96.20 is alive`
    * `192.0.2.0/28 - 192.0.2.1 to 192.0.2.14 are unreachable`

3. List of IPs responding to echo requests:

    `161.35.96.20`

4. Explain which OSI layer(s) your findings involve:

    `Layer 3 Network`

5. Mitigation recommendations (if needed):

    * `Cap the number & rate of ping requests`
    * `Reconfigure firewalls to disallow external pings`
    * `Disable ICMP in extreme cases`

### Phase** 2: _“Some SYN for Nothin`”_**

1. Which ports are open on the RockStar Corp server?

    `Open = 22`
    `Filtered = 80, 554, 646, 1720, 2000`

2. Which OSI layer do SYN scans run on?
    1. OSI Layer:

        `Layer 4 (Transport)`

    2. Explain how you determined which layer:

        `SYN is part of a TCP handshake, with TCP a transport (layer 4) protocol`

3. Mitigation suggestions (if needed):

    * `Block IP Addresses conducting an attack`
    * `Configure firewall for SYN rate-limiting`
    * `Install Intrusion Protection Service (IPS) to monitor network traffic`
    * `Use of SYN cookies`

### Phase** 3: _“I Feel a DNS Change Comin’ On”_**

1. Summarize your findings about why access to rollingstone.com is not working as expected from the RockStar Corp Hollywood office:

    `etc/hosts file on server has been modified to redirect rollingstone.com to ip address 98.137.246.8 (Domain name= unknown.yahoo.com)`

2. Command used to query Domain Name System records:

    `cat /etc/hosts`

3. Domain name findings:

    `rollingstone.com redirects to 98.137.246.8 (Domain name= unknown.yahoo.com)`

4. Explain what OSI layer DNS runs on:

    `Layer 7 (Application)`

5. Mitigation suggestions (if needed):

    * `Remove DNS redirect for rollingstone.com`
    * `Close port 22 and use a more unique port (eg. 34005) for SSH access`
    * `Change SSH login credentials and disable non-admin user login`

### Phase 4: _“ShARP Dressed Man”_

1. Name of file containing packets:

    `secretlogs.pcapng`

2. ARP findings identifying the hacker’s MAC address:

    Frame 5: 42 bytes on wire (336 bits), 42 bytes captured (336 bits) on interface unknown, id 1
Ethernet II, Src: VMware_1d:b3:b1 (00:0c:29:1d:b3:b1), Dst: VMware_fd:2f:16 (00:50:56:fd:2f:16)
Address Resolution Protocol (reply)
    Hardware type: Ethernet (1)
    Protocol type: IPv4 (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: reply (2)
    Sender MAC address: VMware_1d:b3:b1 (00:0c:29:1d:b3:b1)
    Sender IP address: 192.168.47.200
    Target MAC address: VMware_fd:2f:16 (00:50:56:fd:2f:16)
    Target IP address: 192.168.47.2
[Duplicate IP address detected for 192.168.47.200 (00:0c:29:1d:b3:b1) - also in use by `00:0c:29:0f:71:a3 ← Hacker's MAC Address` (frame 4)]
    [Frame showing earlier use of IP address: 4]
        [Expert Info (Warning/Sequence): Duplicate IP address configured (192.168.47.200)]
            [Duplicate IP address configured (192.168.47.200)]
            [Severity level: Warning]
            [Group: Sequence]
    [Seconds since earlier frame seen: 10]

3. HTTP findings, including the message from the hacker:

    * `Hacker has accessed http://www.gottheblues.yolasite.com/\r\n`
    * `Hacker has accessed http://www.gottheblues.yolasite.com/contact-us.php`
    * `Hacker has submitted form "I660593e583e747f1a91a77ad0d3195e3" with contents:

`Name Mr Hacker`
`Email Hacker@rockstarcorp.com`
`Phone`

`Message: Hi Got The Blues Corp!  This is a hacker that works at Rock Star Corp.  Rock Star has left port 22, SSH open if you want to hack in.  For 1 Milliion Dollars I will provide you the user and password!`


4. Explain the OSI layers for HTTP and ARP.
    1. Layer used for HTTP: `Layer 7 (Application)`
        
    2. Layer used for ARP: `Layer 2 (Data Link - MAC Address) & Layer 3 (Network - IP Address)`


5. Mitigation suggestions (if needed):

    * `Secure server SSH access by modifying SSH config file`
    * `Close port 22, change credentials for SSH access, disable non-admin login`
