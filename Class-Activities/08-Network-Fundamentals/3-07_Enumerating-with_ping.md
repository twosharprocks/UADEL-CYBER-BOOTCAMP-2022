## **Wk 8.3 - Activity File: Footprinting with ping**



* In this activity, you will play the role of security analysts at Acme Corp.
* CompuCom, a software company, has hired Acme Corp to do a security assessment of their network.
* CompuCom has provided a list of their host IP addresses. Your task is to use ping to determine which hosts are accepting connections. \



### **Instructions**


1. Use ping to determine which of the following IP addresses are accepting and rejecting connections. \

    * `192.0.43.10 - ACCEPT`
    * `107.191.96.26 - ACCEPT`
    * `41.19.96.234 - TIME OUT`
    * `107.191.101.180 - ACCEPT`
    * `23.226.229.4 - ACCEPT`
    * `154.226.18.4 - TIME OUT`
    * `176.56.238.3  - ACCEPT`
    * `176.56.238.99 - TIME OUT`

2. Use fping to ping all of the IP addresses in a single command.
    * `192.0.43.10 107.191.96.26 41.19.96.234 107.191.101.180 23.226.229.4 154.226.18.4 176.56.238.3 176.56.238.99`

    * `192.0.43.10 is alive`
    * `23.226.229.4 is alive`
    * `107.191.96.26 is alive`
    * `107.191.101.180 is alive`
    * `176.56.238.3 is alive`
    * `41.19.96.234 is unreachable`
    * `154.226.18.4 is unreachable`
    * `176.56.238.99 is unreachable`


### **Bonus**


1. Use fping to ping the range of IPs, from 107.191.96.26 to 107.191.96.32.

`107.191.96.26 is alive`

`107.191.96.27 is alive`

`107.191.96.30 is alive`

`107.191.96.32 is alive`

`107.191.96.28 is unreachable`

`107.191.96.29 is unreachable`

`107.191.96.31 is unreachable`



2. Write a short summary of your findings to provide to CompuCorp.
    1. `7 targets - 4 alive, 3 unreachable (3of3 timeouts)`
