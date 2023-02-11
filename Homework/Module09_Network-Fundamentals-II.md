## In a Network Far, Far Away!

Make a copy of this document to work in, and then for each mission, add the solution below the prompt. Save and submit this completed file as your Challenge deliverable.


### Mission 1


1. Mail servers for starwars.com:

`aspmx2.googlemail.com`
`alt1.aspx.l.google.com`
`aspmx3.googlemail.com`
`aspmx.l.google.com`
`alt2.aspmx.l.google.com`


2. Explain why the Resistance isn’t receiving any emails:

    `Primary mail server should be asltx.l.google.com with asltx.2.google.com as secondary, however nslookup on starwars.com shows the highest priority mailserver is aspmx.l.google.com (1) with alt1.aspmx.l.google.com & alt2.aspmx.l.google.com as secondaries`


3. Suggested DNS corrections:

    `Access domain host account and configure DNS MX record to point to correct MX servers`




### Mission 2



1. Sender Policy Framework (SPF) of `theforce.net`:

    `v=spf1 a mx a:mail.wise-advice.com mx:smtp.secureserver.net include:aspmx.googlemail.com ip4:104.156.250.80 ip4:45.63.15.159 ip4:45.63.4.215  ip4:104.207.135.156 ~all`


2. Explain why the Force’s emails are going to spam:

    `theforce.net lists their mail server as 45.23.176.21 however the SPF identifies 4 other IP addresses (104.156.250.80, 45.63.15.159, 45.63.4.215 , and 104.207.135.156) which does not include 45.23.176.21`


3. Suggested DNS corrections:

    `Add 45.23.176.21 to the SPF for theforce.net`




### Mission 3



1. Document the CNAME records:

    `$ nslookup -q=cname www.theforce.net`
    `Server:         10.0.2.3`
    `Address:        10.0.2.3#53`
    `www.theforce.net        canonical name = theforce.net.`


2. Explain why the subpage `resistance.theforce.net` isn’t redirecting to `theforce.net`:

    `theforce.net does not have any CNAME recordsfanart`


3. Suggested DNS corrections:

    `Access domain DNS records and create CNAME record pointing to resistance.theforce.net`


### Mission 4



1. Confirm the DNS records for `princessleia.site`:

    `$ nslookup princessleia.site`
    `Server:         10.0.2.3`
    `Address:        10.0.2.3#53`
    
    `Non-authoritative answer:`
    `Name:   princessleia.site`
    `Address: 34.102.136.180`
    `Name:   princessleia.site`
    `Address: 20.40.202.19`

2. Suggested DNS record corrections to prevent the issue from occurring again:

    `Access domain DNS records and configure princessleia.site to have ns2.galaxybackup.com as a secondary DNS server`




### Mission 5



1. Document the shortest `OSPF` path from Batuu to Jedha:
    1. `OSPF` path:

        `Batuu-D-C-F-J-K-N-O-R-U-V-Jedha`


    2. `OSPF` path cost:

        `26`




### Mission 6

1. Wireless key:

    `dictionary`


2. Host IP addresses and MAC addresses:
    1. Sender MAC address:

        `00:0f:66:e3:e4:01`


    2. Sender IP address:

        `172.16.0.1`


    3. Target MAC address:

        `00:13:ce:55:98:ef`


    4. Target IP address:

        `172.16.0.101`




### Mission 7

1. Screenshot of results:
