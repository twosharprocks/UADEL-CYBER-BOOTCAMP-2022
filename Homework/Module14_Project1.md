## Your Web Application

## Day 1 Questions


### General Questions



1. What option did you select for your domain (Azure free domain,  GoDaddy domain)?

    `GoDaddy `


2. What is your domain name?

    `www.twosharprocks.com.au`




### Networking Questions



1. What is the IP address of your webpage?

    `20.211.64.15`


2. What is the location (city, state, country) of your IP address?

    `Sydney, New South Wales, Australia`


3. Run a DNS lookup on your website. What does the NS record show?

    `ns37.domaincontrol.com TTL=3600
ns38.domaincontrol.com TTL=3600`




### Web Development Questions



1. When creating your web app, you selected a runtime stack.  What was it? Does it work on the front end or the back end? 

    `PHP 8.2`


2. Inside the `/var/www/html` directory, there was another directory called assets. Explain what was inside that directory.

    `The images and CSS (assests) of the website`


3. Consider your response to the above question. Does this work with the front end or back end?

    `Front end`




## Day 2 Questions


### Cloud Questions



1. What is a cloud tenant?

    `An individual or organisation with a presence within a cloud environment. `


2. Why would an access policy be important on a key vault?

    `Helps restrict access to authorised users and applications, and allows differing levels of access depending on individual user privilege. It also provides a way of logging key vault access in the event of a security breach. `


3. Within the key vault, what are the differences between keys, secrets, and certificates?

    `Keys are cryptographic keys for encryption and digital signatures, secrets are sensitive data like passwords, and certificates are used for authentication and authorisation.`




### Cryptography Questions



1. What are the advantages of a self-signed certificate?

    `Self-signed certificates are free, easy to create, and quick to implement.`


2. What are the disadvantages of a self-signed certificate?

    `Self-signed certificates are not trusted by default by web browsers or applications.`


3. What is a wildcard certificate?

    `A certificate with a wildcard character in the domain name field which allows it to secure multiple sub-domain names.`


4. When binding a certificate to your website, Azure only provides TLS versions 1.0, 1.1, and 1.2.  Explain why SSL 3.0 isn’t provided.

    `SSL 3.0 has a vulnerability known as POODLE which allows an attacker to decrypt and extract information from an encrypted transmission.`


5. After completing the Day 2 activities, view your SSL certificate and answer the following questions:
    1. Is your browser returning an error for your SSL certificate? Why or why not?

        `No error. The SSL certificate has been verified and is working normally.`


    2. What is the validity of your certificate (date range)?

        `10/11/2006 to 10/11/2031`


    3. Do you have an intermediate certificate? If so, what is it?

        `Yes - Go Daddy Secure Certificate Authority`


    4. Do you have a root certificate? If so, what is it?

        `Yes - Go Daddy Root Certificate Authority - G2`


    5. Does your browser have the root certificate in its root store?

        `Yes`


    6. List one other root CA in your browser’s root store.

        `D-TRUST Root Class 3 CA 2 2009`




## Day 3 Questions


### Cloud Security Questions 



1. What are the similarities and differences between Azure Web Application Gateway and Azure Front Door?

    `Both offer: load balancing, SSL/TLS encryption, health checks and traffic routing. 
Their differences are: Front Door is a Content Delivery Network (CDN) intended for global traffic management with geo-redundancy, caching, and load balancing operating on OSI layer 4; whereas Web Application Gateway is designed specifically for web applications and has application firewalls (OSI layer 7)`


2. A feature of the Web Application Gateway and Front Door is “SSL Offloading.” What is SSL offloading? What are its benefits?

    `Terminating SSL/TLS encryption at a network device then forwarding the unencrypted traffic to the server. This improves server performance, centralises security, and simplifies certificate management`


3. What OSI layer does a WAF work on?

    `Layer 7 (Application)`


4. Select one of the WAF managed rules (e.g., directory traversal, SQL injection, etc.), and define it.

    `Remote Command Execution: Unix Command Injection - Injecting malicious UNIX commands in order to disrupt, destroy, or extract information stored in the OS`


5. Consider the rule that you selected. Could your website (as it is currently designed) be impacted by this vulnerability if Front Door wasn’t enabled? Why or why not?

    `Yes my website could be impacted without Front Door enabled, as the web app is hosted on a unix-based OS (Ubuntu) and uses a unix-like command terminal for website updates and management.`


6. Hypothetically, say that you create a custom WAF rule to block all traffic from Canada. Does that mean that anyone who resides in Canada would not be able to access your website? Why or why not? 

    `Not necessarily - the traffic is likely to bounce off several nodes prior to arrival at my WAF, and only traffic coming directly from Canada to the WAF will be blocked. Someone in Canada having ocnnection issues could also use a VPN to bypass the custom WAF rule`
