Project 1) 
Commands:- sudo apt update
sudo apt install dvwa
sudo dvwa-start


Project 3:- AUTOMATED VS MANUAL SCANNING
Target application: OWASP juice shop
url:http://127.0.0.1:3000 
on kali linux

Tools used 1)Nikto 
2) OWASP
3)sqlmap
4) burpsuite

Results of Nikto 
Command:- nikt -h http://127.0.0.1:3000
findings:- Missing security headers.

Information disclosure related to server configuration

Potentially dangerous HTTP methods enabled





2. OWASP ZAP Active Scan

Steps:

ZAP Quick Start → Automated Scan

Target URL: http://127.0.0.1:3000


Findings:

Reflected XSS alerts on search functionality

Missing Content Security Policy (CSP)

Cookie security flags missing



---

3. sqlmap Testing

Command Used:

sqlmap -u "http://127.0.0.1:3000/rest/products/search?q=apple" --level=2 --risk=2

Result:

Parameter q was not injectable

sqlmap output showed: all tested parameters do not appear to be injectable



Manual Testing Results (Burp Suite)

1. Manual XSS Testing
Result:

JavaScript alert popup triggered

Confirmed Reflected XSS vulnerability



2. Manual SQL Injection / Logic Testing

Location: Login page

Payload Used:

' OR 1=1--

Password: test

Result:


Login bypass attempt failed
secure

COMPARISION AUTOMATED VS MANUAL

Issues Found by Automated Tools

Missing security headers

Reflected XSS indicators

General misconfigurations


Issues Found by Manual Testing

Confirmed XSS execution via browser



4) Whatweb fingerprinting
   command:- whatweb http://localhost/dvwa

   Dirb directory scan
   command:- dirb http://localhost/dvwa

   Nuclei scan
   command:- nuclei -u http://localhost/dvwa


5) IDOR (Insecure direcot object reference)
   (Performing Idor)
   steps
   a) vist (owasp juice shop)
   b) login and open network tab
   c) click get then go to responce
   d) change data
   e) if you get data of another user then it is idor.


   
Checking Security headers 

command:- curl -I http://localhost/dvwa

Gathering Sensitive information using JS
STEPS:- 

Open any website
press right button, go to inspection
then Sources 
then press Ctrl+F and search keywords like, apiKey, token, password, secret, username.



















