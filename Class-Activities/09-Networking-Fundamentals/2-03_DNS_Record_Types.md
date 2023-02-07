## **Activity File: Analyzing DNS Record Types**

In this activity, you will play the role of a security analyst at Acme Corp.

* Acme Corp recently updated the DNS records for several of their sites and needs you to confirm the updates worked.

* Your task is to use nslookup to validate the DNS records for each of the domains provided.

### **Instructions**

1. Acme Corp owns the following domains:

    * splunk.com
    * fireeye.com
    * nmap.org
2. For each website, determine the following DNS records and document your findings:

    * A record
    * NS record
    * MX record

    * splunk.com
        1. `A= 52.5.196.118`
        2. `NS= ha1.markmonitor.zone ha2.markmonitor.zone ha3.markmonitor.zone ha4.markmonitor.zone`
        3. `MX= mx1.splunk.iphmx.com mx2.splunk.iphmx.com`
    * fireeye.com 
        4. `A= 162.159.246.125`
        5. `NS= bonnie.ns.cloudflare.com & chuck.ns.cloudflare.com`
        6. `MX= alt3.us.email.fireeyecloud.com primary.us.email.fireeyecloud.com alt1.us.email.fireeyecloud.com alt2.us.email.fireeyecloud.com`
    * nmap.org 
        7. `A= 45.33.49.119`
        8. `NS= ns1.linode.com ns2.linode.com ns3.linode.com ns4.linode.com ns5.linode.com`
        9. `MX= ASPMX.L.GOOGLE.COM ASPMX2.GOOGLEMAIL.COM ASPMX3.GOOGLEMAIL.COM ALT1.ASPMX.L.GOOGLE.COM ALT2.ASPMX.L.GOOGLE.COM`
3. Answer the following questions:

 a. Did any of the domains have more than one MX record? If so, why do you think that is? `All of them as redundancy`
 
 b. For nmap.org, list the mail servers, from the highest to lowest priority.
 
    * 1. `ASPMX.L.GOOGLE.COM`
    * 2. `ALT1.ASPMX.L.GOOGLE.COM` 
    * 3. `ALT2.ASPMX.L.GOOGLE.COM` 
    * 4. `ASPMX2.GOOGLEMAIL.COM` 
    * 5. `ASPMX3.GOOGLEMAIL.COM`
