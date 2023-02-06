## **Activity File: Distribution Research** {#activity-file-distribution-research}



* Recently, your organization experienced a number of breaches involving servers running outdated Linux distributions. \

* In response, the IT Department has decided to upgrade the affected servers, and chose you as the **system administrator** in charge of deciding which distribution to install on each machine. \

* In this exercise, you will research the most common distributions of Linux and answer the following questions. Then you will use what you learn to determine which distribution is most appropriate for each machine on the network. \


Be sure to ask your instructors and classmates for help if you get stuck.


### **A. Resources and Research** {#a-resources-and-research}

Use the following links to answer the questions below:



* [Debian Linux](https://www.debian.org/intro/about)
* [Ubuntu Linux](https://www.ubuntu.com/download)
* [Kali Linux](https://www.kali.org/about-us/)
* [RedHat](https://www.redhat.com/en/technologies)
* [Fedora](https://getfedora.org/)
* [CentOS](https://www.centos.org/about/)
* [SELinux](https://selinuxproject.org/page/Main_Page)
* [Mint Breach](https://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/)


### **Questions** {#questions}



1. Which distribution is most flexible and best suited for day-to-day and administrative tasks? (Ubuntu, Fedora, Debian, Linux Mint) \

2. Which distribution is built specifically for penetration testers? (Kali Linux) \

3. Which distributions would you use to set up a web or data server? (Ubuntu Server) \

4. What is the most widely used Linux desktop environment? (Ubuntu) \



### **B. Use Cases** {#b-use-cases}

Identify which distribution(s) is most appropriate for each situation. There may be more than one correct answer.

**Central Data Server**



* The Central Data Server stores all human resources data, including payroll information. Since its sole purpose is to send data to other machines, it won't have a monitor attached, and doesn't need a GUI. (Ubuntu Server, CentOS, Debian, OpenSUSE)

**Public Web Server**



* The Public Web Server must handle a large number of requests every day. It also doesn't need a GUI. Since the Web Server is central to business operations, it needs to run very quickly. (Ubuntu Server, CentOS, Debian, OpenSUSE)

**IT Audit Workstation**



* The IT Audit Workstation is used for periodic assessments of the security of the network. (Kali, Ubuntu)

**User Workstations**



* User Workstations need a GUI, and should include basic productivity software (such as LibreOffice, email clients, etc.) (Ubuntu, Debian, Fedora, Mint)


### **Bonus Questions** {#bonus-questions}



1. What is a "headless server"? (No Monitor, keyboard or mouse) Does Ubuntu make a headless server variant? (Yes - Ubuntu Server) What about Fedora? (No but can install headless) CentOS? \

2. What distribution is Ubuntu based on? (Debian) What about Kali? (Backtrack, Debian) \

3. Which distribution is CentOS based on? (Red Hat) What about Fedora? (Red Hat) \

4. What is SELinux? (Security-Enchanced Linux, derived from NSA) Which distributions implement SELinux by default? Fedora, Ubuntu, OpenSUSE, Debian, \

5. If you were deciding between versions of Ubuntu Server and wanted one that would remain stable over time, which version would you choose? (22.04.01) \

6. What are some security implications of using free and open source software or forks of popular Linux distributions? (As OSS is publicly available, ensuring quality and maintenance is only possible with proactive community efforts. OSS is also less secure than proprietary codes as it’s vulnerable to exploitation. When security issues are identified, they’re made public. Compared to proprietary software with controlled access to code, OSS is inherently easier for cyberattackers to exploit.)
