## Web Development

Make a copy of this document to work in, and then respond to each question below the prompt. Save and submit this completed file as your Challenge deliverable.


### HTTP Requests and Responses



1. What type of architecture does the HTTP request and response process occur in?

    `Client-Server`


2. What are the parts of an HTTP request?

    `Request Line, Headers, and Request Body`


3. Which part of an HTTP request is optional?

    `Request body`


4. What are the three parts of an HTTP response?

    `Status line, headers, response body`


5. Which status-code number class represents errors?

    `4xx (Client-error) and 5xx (Server-error)`


6. What are the two most common request methods for a security professional to encounter?

    `GET and POST`


7. Which type of HTTP request method is used to send data?

    `POST`


8. Which part of an HTTP request contains the data being sent to the server?

    `Request Body`


9. In which part of an HTTP response does the browser receive the web code to generate and style a webpage?

    `Response Body`




### Using cURL



10.  What are the advantages of using `curl` over the browser?

    `Allows automated HTTP request testing, or use through a container with no user interface`


11. Which `curl` option changes the request method?

`-X`


12.  Which `curl` option sets request headers?

`-H`


13.  Which `curl` option is used to view the response header?

`-v`


14. Which request method might an attacker use to figure out what HTTP requests an HTTP server will accept?

    `OPTIONS`




### Sessions and Cookies



15.  Which response header sends a cookie to the client?

    `HTTP/1.1 200 OK`
    `Content-type: text/html`
    `Set-Cookie: cart=Bob`

Answer `“Set-Cookie” header sends a cookie to the client`

16.  Which request header will continue the client's session?

    `GET /cart HTTP/1.1`
    `Host: www.example.org`
    `Cookie: cart=Bob`

Answer `“Cookie: cart=Bob” maintains the client’s session`


### Example HTTP Requests and Responses

Use the following sample HTTP request and response to answer the questions in this section:

**HTTP Request**


```
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```




17.  What is the request method?

    `POST`


18.  Which header expresses the client's preference for an encrypted response?

    `Upgrade-Insecure-Requests: 1`


19.  Does the request have a user session associated with it?

    `No`


20.  What kind of data is being sent from this request body?

    `Username and password`



**HTTP Response**


```
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```




21.  What is the response status code?

    `200 OK`


22.  What web server is handling this HTTP response?

    `Apache`


23.  Does this response have a user session associated with it?

    `Yes, SessionID=5`


24.  What kind of content is likely to be in the [page content] response body?

    `text/html encoded in UTF-8 charset`


25.  If your class covered security headers, what security request headers have been included?

    `Strict-Transport-Security, X-Content-Type, X-Frame-Options, XSS-Protection`




### Monoliths and Microservices



26. What are the individual components of microservices called?

    `Store App UI (Front-End), User API (Back-End), User Database`


27. What is a service that writes to a database and communicates to other services?

    `Back-End`


28. What type of underlying technology allows for microservices to become scalable and have redundancy?

    `Containers`




### Deploying and Testing a Container Set



29. What tool can you use to deploy multiple containers at once?

    `Docker`


30. What kind of file format is required to deploy a container set?

    `YAML (.yml) configuration file`




### Databases



31. Which type of SQL query would you use to view all of the information within a table called `customers`?

    `SELECT * FROM customers`


32. Which type of SQL query would you use to enter new data into a table? (You don't need a full query, just the first part of the statement.)

    `INSERT INTO table_name (Column1, Column 2, ect) VALUES (value1, value2, ect)`


33.  Why would you never run `DELETE FROM &lt;table-name>;` by itself?

    `It would delete the entire table as there is no WHERE statement`




### Bonus Activity: The Cookie Jar

**Question 1**: Did you see any obvious confirmation of a login? (Y/N)


```
[Enter answer here]
```


**Question 2**: How many items exist in this file?


```
[Enter answer here]
```


**Question 3**: Is it obvious that you can access the dashboard? (Y/N)


```
[Enter answer here]
```


**Question 4**: Look through the output where `Dashboard` is highlighted. Does any of the wording on this page seem familiar? (Y/N) If so, you should be successfully logged in to your Editor's dashboard.


```
[Enter answer here]
```


**Question 5**: What happens this time?

  <tr>
   <td>

```
[Enter answer here]
```


   </td>
  </tr>
