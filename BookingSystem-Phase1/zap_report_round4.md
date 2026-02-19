# zap_report_round4

ZAP by [Checkmarx](https://checkmarx.com/).


## Summary of Alerts

| Risk Level | Number of Alerts |
| --- | --- |
| High | 0 |
| Medium | 0 |
| Low | 0 |
| Informational | 3 |




## Insights

| Level | Reason | Site | Description | Statistic |
| --- | --- | --- | --- | --- |
| Medium | Exceeded Low |  | Percentage of memory used | 92    |
| Low | Warning |  | ZAP warnings logged - see the zap.log file for details | 18    |
| Info | Informational | http://localhost:8004 | Percentage of responses with status code 2xx | 63 % |
| Info | Informational | http://localhost:8004 | Percentage of responses with status code 3xx | 31 % |
| Info | Informational | http://localhost:8004 | Percentage of responses with status code 4xx | 4 % |
| Info | Informational | http://localhost:8004 | Percentage of endpoints with content type application/javascript | 25 % |
| Info | Informational | http://localhost:8004 | Percentage of endpoints with content type text/css | 6 % |
| Info | Informational | http://localhost:8004 | Percentage of endpoints with content type text/html | 31 % |
| Info | Informational | http://localhost:8004 | Percentage of endpoints with content type text/plain | 12 % |
| Info | Informational | http://localhost:8004 | Percentage of endpoints with method GET | 81 % |
| Info | Informational | http://localhost:8004 | Percentage of endpoints with method POST | 18 % |
| Info | Informational | http://localhost:8004 | Count of total endpoints | 16    |
| Info | Informational | http://localhost:8004 | Percentage of slow responses | 1 % |




## Alerts

| Name | Risk Level | Number of Instances |
| --- | --- | --- |
| Authentication Request Identified | Informational | 1 |
| Session Management Response Identified | Informational | 3 |
| User Agent Fuzzer | Informational | Systemic |




## Alert Detail



### [ Authentication Request Identified ](https://www.zaproxy.org/docs/alerts/10111/)



##### Informational (High)

### Description

The given request has been identified as an authentication request. The 'Other Info' field contains a set of key=value lines which identify any relevant fields. If the request is in a context which has an Authentication Method set to "Auto-Detect" then this rule will change the authentication to match the request identified.

* URL: http://localhost:8004/login
  * Node Name: `http://localhost:8004/login ()(csrf_token,password,username)`
  * Method: `POST`
  * Parameter: `username`
  * Attack: ``
  * Evidence: `password`
  * Other Info: `userParam=username
userValue=foo-bar@example.com
passwordParam=password
referer=http://localhost:8004/login
csrfToken=csrf_token`


Instances: 1

### Solution

This is an informational alert rather than a vulnerability and so there is nothing to fix.

### Reference


* [ https://www.zaproxy.org/docs/desktop/addons/authentication-helper/auth-req-id/ ](https://www.zaproxy.org/docs/desktop/addons/authentication-helper/auth-req-id/)



#### Source ID: 3

### [ Session Management Response Identified ](https://www.zaproxy.org/docs/alerts/10112/)



##### Informational (Medium)

### Description

The given response has been identified as containing a session management token. The 'Other Info' field contains a set of header tokens that can be used in the Header Based Session Management Method. If the request is in a context which has a Session Management Method set to "Auto-Detect" then this rule will change the session management to use the tokens identified.

* URL: http://localhost:8004/login
  * Node Name: `http://localhost:8004/login`
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `csrf_token`
  * Other Info: `cookie:csrf_token`
* URL: http://localhost:8004/register
  * Node Name: `http://localhost:8004/register`
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `csrf_token`
  * Other Info: `cookie:csrf_token`
* URL: http://localhost:8004/login
  * Node Name: `http://localhost:8004/login`
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `csrf_token`
  * Other Info: `cookie:csrf_token`


Instances: 3

### Solution

This is an informational alert rather than a vulnerability and so there is nothing to fix.

### Reference


* [ https://www.zaproxy.org/docs/desktop/addons/authentication-helper/session-mgmt-id/ ](https://www.zaproxy.org/docs/desktop/addons/authentication-helper/session-mgmt-id/)



#### Source ID: 3

### [ User Agent Fuzzer ](https://www.zaproxy.org/docs/alerts/10104/)



##### Informational (Medium)

### Description

Check for differences in response based on fuzzed User Agent (eg. mobile sites, access as a Search Engine Crawler). Compares the response statuscode and the hashcode of the response body with the original response.

* URL: http://localhost:8004/login
  * Node Name: `http://localhost:8004/login`
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8004/register
  * Node Name: `http://localhost:8004/register`
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8004/reservation
  * Node Name: `http://localhost:8004/reservation`
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8004/login
  * Node Name: `http://localhost:8004/login ()(csrf_token,password,username)`
  * Method: `POST`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8004/register
  * Node Name: `http://localhost:8004/register ()(birthdate,csrf_token,password,role,username)`
  * Method: `POST`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)`
  * Evidence: ``
  * Other Info: ``

Instances: Systemic


### Solution



### Reference


* [ https://owasp.org/wstg ](https://owasp.org/wstg)



#### Source ID: 1


