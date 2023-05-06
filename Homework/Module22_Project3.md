# Project 3 Review Questions


## Windows Server Log Questions

## Report Analysis for Severity

* Did you detect any suspicious changes in severity?

`Yes - Increase in "High" severity events from 6.9% to 20.2%`
`"Informational" events dropped from 93.1% to 79.8%`



## Report Analysis for Failed Activities



* Did you detect any suspicious changes in failed activities?

`Yes - Increase in median of failures from 20 to 28`


## Alert Analysis for Failed Windows Activity



* Did you detect a suspicious volume of failed activity?

`Yes`


*  If so, what was the count of events in the hour(s) it occurred?

`140 Failures`



*  When did it occur?

`0800 on 25 March 2020`


*  Would your alert be triggered for this activity?

`Yes - it's set to fire when failures exceed 100 in an hour`


*  After reviewing, would you change your threshold from what you previously selected?

`No`



   

## Alert Analysis for Successful Logins



*  Did you detect a suspicious volume of successful logins?

`Yes`

*  If so, what was the count of events in the hour(s) it occurred?

`1100-1200 - 196 Successful logins `
`1200-1300 - 77 Successful logins`



*  Who is the primary user logging in?

`User_j with 69.907% of the logins`



*  When did it occur?

`1100-1300`


*  Would your alert be triggered for this activity?

`Yes`


*  After reviewing, would you change your threshold from what you previously selected?

`No`




## Alert Analysis for Deleted Accounts



* Did you detect a suspicious volume of deleted accounts?  

`No`


## Dashboard Analysis for Time Chart of Signatures

*    Does anything stand out as suspicious?

`Yes`

* What signatures stand out?

`Signature_id=4724 "An attempt was made to reset an accounts password"`
`Signature_id=4740 "A user account was locked out"`
`Signature_id=4624 "An account was successfully logged on"`


* What time did it begin and stop for each signature?

`Signature_id=4724 - 0100 to 0300 on 25 March 2020`
`Signature_id=4740 - 0900 to 1100 on 25 March 2020`
`Signature_id=4624 - 1100 to 1200 on 25 March 2020`


*    What is the peak count of the different signatures?

`Signature_id=4724 - 1258 signatures`
`Signature_id=4740 - 896 signatures`
`Signature_id=4624 - 196 signatures`



## Dashboard Analysis for Users



*    Does anything stand out as suspicious?

    `Significant increase in user privilege changes between 0100-0300 and between 0900-1100, with a baseline of 70 per hour jumping to 339 and 366`


*    Which users stand out?

`user_a`
`user_k`
`user_j`


*    What time did it begin and stop for each user?

    `user_a between 0100-0300 on 25 March 2020`
    `user_k between 0900-1100 on 25 March 2020`
    `user_j between 1100-1200 on 25 March 2020`


*    What is the peak count of the different users?

    `user_a with 984 events`
    `user_k with 1256 events`
    `user_j with 196 events`

##  Dashboard Analysis for Signatures with Bar, Graph, and Pie Charts



*    Does anything stand out as suspicious?

    `Peaks in activity around 0200 and 0900 on 25 March 2020`


*    Do the results match your findings in your time chart for signatures?    

    `Yes`



** Dashboard Analysis for Users with Bar, Graph, and Pie Charts  **   



*    Does anything stand out as suspicious?

    `user_a and user_k make up 67.1% of all logins `


*    Do the results match your findings in your time chart for users?

    `Yes`



## Dashboard Analysis for Users with Statistical Charts**

* What are the advantages and disadvantages of using this report, compared to the other user panels that you created?

    `Advantages: Easy identification of event peaks and potential attack signatures`
    `Disadvantages: Only represents most significant peaks and events in detail`




# Apache Web Server Log Questions

##  Report Analysis for Methods



*  Did you detect any suspicious changes in HTTP methods? If so, which one?

    `Yes. The number of POST requests has gone up to nearly 30%(29.44%) from 1% as it showed in Apache log. GET requests have dropped from 98% from apache_log to 70% in apache-attack_log`


* What is that method used for?


`The POST method is commonly used in web applications to submit forms or upload files. When a user submits a form, the form data is sent to the server using a POST request, which typically includes the data in the request body. The server can then process the data and return a response, which can be used to update the application's state or display a confirmation message to the user.`
`The POST method can also be used to create new resources on the server. For eg: if an application allows users to create new accounts, the user data can be sent to the server using a POST request, and the server can create a new user account based on the data provided.`


## Report Analysis for Referrer Domains



*    Did you detect any suspicious changes in referrer domains?

    `No.`



## Report Analysis for HTTP Response Codes



*  Did you detect any suspicious changes in HTTP response codes? 

    `Yes. The response code 416 happened to be existing only in apache log file twice. The status code means Requested range is not satisfiable. Meaning the request made was out of company bounds.`



## Alert Analysis for International Activity



*  Did you detect a suspicious volume of international activity?

    `Yes`


*  If so, what was the count of the hour(s) it occurred in?

    `884 counts between 2000-2100 on 25 March 2020`


*  Would your alert be triggered for this activity?

    `Yes`


*  After reviewing, would you change the threshold that you previously selected?

    `No`



## Alert Analysis for HTTP POST Activity



*  Did you detect any suspicious volume of HTTP POST activity?

    `Yes`


*  If so, what was the count of the hour(s) it occurred in?

    `1296 events`


*  When did it occur?

    `2000-2100 on 25 March 2020`


*  After reviewing, would you change the threshold that you previously selected?  

    `No`



## Dashboard Analysis for Time Chart of HTTP Methods



*  Does anything stand out as suspicious?

    `Significant increase in the number of GET requests at 1800 on 25 March 2020`
    `Significant increase in the number of POST requests at 2000 on 25 March 2020`


*  Which method seems to be used in the attack?

    `POST method, as POST is how data is uploaded over HTTP. GET requests are only used to deliver existing information from the server`


*  At what times did the attack start and stop?

    `2000-2100 on 25 March 2020`


*  What is the peak count of the top method during the attack?

    


`1296 POST requests`


## Dashboard Analysis for Cluster Map**



*  Does anything stand out as suspicious?

    `Significant increase in client IPs originating from Ukraine`


*  Which new location (city, country) on the map has a high volume of activity? (**Hint**: Zoom in on the map.)

    `Kiev`


*  What is the count of that city?

    


`438`


## Dashboard Analysis for URI Data



*  Does anything stand out as suspicious?

    `Significant increase in overall URI counts, with specific peaks for /VSI_Account_logon.php and /files/logstash/logstash-1.3.2-monolithic.jar
`

*  What URI is hit the most?

    `/VSI_Account_logon.php`


*  Based on the URI being accessed, what could the attacker potentially be doing?

    `A brute-force login attempt on the Apache server`
