## **Wk 8.3 - Activity File: Analyzing TCP Traffic**

In this activity, you will continue to play the role of a security analyst at Acme Corp.


* CompuCom, a software company, has hired Acme Corp to do a security assessment of its network. \

* CompuCom has requested that you analyze a new employee's TCP traffic to determine what they're working on during their first week. \


### **Instructions**


1. Open the packet capture provided and filter out for TCP activity. \

2. Find all the TCP handshakes for establishing a connection.
    * 1	`2019-07-10 23:16:41.271613793	10.0.2.15	52.26.234.148	TCP	74	42898 → 80 [SYN] Seq=0 Win=29200 Len=0 MSS=1460 SACK_PERM TSval=1923727876 TSecr=0 WS=128`
        1. `CONNECTION TO AMAZON AWS`
    * 4	`2019-07-10 23:16:43.852736428	10.0.2.15	8.35.179.200	TCP	74	34654 → 80 [SYN] Seq=0 Win=29200 Len=0 MSS=1460 SACK_PERM TSval=3666086224 TSecr=0 WS=128`
        2. `CONNECTION TO ISP IN MONROE, LOUISIANA`
    * 7	`2019-07-10 23:16:54.189678957	10.0.2.15	209.202.133.24	TCP	74	57176 → 80 [SYN] Seq=0 Win=29200 Len=0 MSS=1460 SACK_PERM TSval=3070900123 TSecr=0 WS=128`
        3. `CONNECTION TO National Leisure Group (Cruise trips)`
3. Find any TCP terminations.
    * 10	`2019-07-10 23:17:00.294279042	209.202.133.24	10.0.2.15	TCP	60	80 → 57178 [FIN, ACK] Seq=1 Ack=1 Win=65535 Len=0`
4. Use your findings to determine what the employee is doing during their first week of work. - `LOOKING UP CRUISE TRIPS WITH NATIONAL LEISURE COMPANY`[ \
](https://securitytrails.com/domain/example.com/dns)
