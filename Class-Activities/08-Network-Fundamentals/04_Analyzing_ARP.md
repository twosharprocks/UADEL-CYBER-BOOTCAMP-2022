## **Wk 8.3 - Activity File: Analyzing ARP**

In this activity, you will play the role of a security analyst at Acme Corp.

* CompuCom, a software company, has hired Acme Corp to do a security assessment of their network.
* Your task is to analyze ARP activity from a CompuCom packet capture to determine if any vulnerabilities exist


### **Instructions**

1. Open the packet capture provided to you and filter out for ARP activity.
2. Document the physical addresses found for each of the following IP addresses:
    * 192.168.47.1 → `00:50:56:c0:00:08 (VMWare)`
    * 192.168.47.2 → `00:50:56:fd:2f:16 (VMWare)`
    * 192.168.47.200 → `00:0c:29:0f:71:a3 (VMWare)`
    * 192.168.47.254 → `00:50:56:f9:f5:54 (VMWare)` 
3. Further analyze the packet capture to determine if these IPs present any potential security vulnerabilities, and write summary of your findings to provide to CompuCorp.
    `ARP Spoofing: Man-In-The-Middle attack occuring to map IPs to 00:0c:29:1d:b3:b1`


#### **Bonus**



1. Name a few ways to protect against this vulnerability.
    1. `Physical/Access Point Security`
    2. `Switch Security (Dynamic ARP Inspection)`
    3. `Static ARP Tables`
    4. `Network Isolation`
    5. `Encryption`
2. Determine the primary vendor for the MAC addresses.
    6. `VMWare`
