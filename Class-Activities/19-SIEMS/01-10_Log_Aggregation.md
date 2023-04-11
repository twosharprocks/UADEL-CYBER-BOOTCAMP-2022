## Activity File: Log Aggregation and Normalization

 You will continue to play the role of an SOC manager at OMP.

- Your CIO would like you to focus on monitoring web server logs, as OMP has recently experienced DOS attempts.

- Each web server logs data in a different format. You must aggregate and normalize the logs by identifying the various fields in the log files.


### Instructions

You have been provided one log record from each web server to help you normalize the logs.

Identify the various fields from each log record. The fields include:
   - Date
   - IP
   - Resource Requested
   - User Agent
   - HTTP Response Code
   - File Size
   - Protocol and Version

**Hint:**  Use Google to research the fields you aren't familiar with.

`Standardise to JSON`

`Log Record 1`
{
    "timestamp": "2015-05-17T10:05:12Z",
    "request_method": "GET",
    "request_url": "/presentations/logstash",
    "http_version": "HTTP/1.1",
    "response_code": 200,
    "response_size": 7697,
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 19_9_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/32.23.34.77 Safari/537.36",
    "ip_address": "83.149.9.216"
}

`Log Record 2`
{
    "timestamp": "2019-05-18T10:05:12Z",
    "request_method": "GET",
    "request_url": "/presentations/newfile.js",
    "http_version": "HTTP/1.1",
    "response_code": 200,
    "response_size": 7697,
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/32.0.1700.77 Safari/537.36",
    "ip_address": "151.32.9.84"
}

`Log Record 3`
{
    "timestamp": "2015-05-15T10:05:12Z",
    "request_method": "GET",
    "request_url": "/presentations/extrafile.js",
    "http_version": "HTTP/1.1",
    "response_code": 200,
    "response_size": 7697,
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/32.0.234344.77 Safari/537.36",
    "ip_address": "35.19.88.100"
}

---
