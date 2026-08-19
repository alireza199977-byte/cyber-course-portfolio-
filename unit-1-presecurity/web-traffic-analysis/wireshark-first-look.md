Wireshark First Look — Worksheet Answers
Part A — HTTP Capture (U1-03a_http_login.pcap)
1. Find the login submission. What username and password were sent? Paste the line from the stream where you found them.
username=anna.virtanen&password=Summer2026!&remember=on
2. The login form was submitted using which HTTP method — GET or POST?
POST /login HTTP/1.1
Host: lab-portal.local
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Content-Type: application/x-www-form-urlencoded
Content-Length: 55
Connection: keep-alive
Answer: POST
The credentials are in the HTTP body, not the URL.

3. After a successful login, the server sends back a Set-Cookie header. What is the value of the SESSIONID cookie? Why might an attacker who sees this cookie be dangerous, even without the password?

Set-Cookie: SESSIONID=a3f9c2e7b81d4f60a5e2c9d10f4b7e88; Path=/; HttpOnly
Answer:  
A session cookie is your login.
If an attacker steals this SESSIONID, they can impersonate the user immediately — no password required.
This is called session hijacking, because the server trusts the cookie as proof of authentication.

4. The dashboard page reveals personal details about the user. List two pieces of sensitive information visible there.
Full name: Anna Virtanen

Email: anna.virtanen@pohjola-logistics.local

(Also visible: Role and last login IP address.)

Part B — HTTPS Capture (U1-03a_https_login.pcap)
5. Apply the filter tls. Can you find the username and password? Why or why not?
Answer: No — the data is encrypted.

Example of encrypted TLS stream:

....N...J......l%..k=.P...@....'..e..
........./.0.................lab-portal.local
....*...&......!}
3..(.:..)......G.....T.<.../.....K...G..D..A0..=0..%.......w.M...sj.......(!a
6. What server name is visible in the Client Hello (SNI)?
Code
lab-portal.local
7. Even though contents are encrypted, what can an eavesdropper still learn?
IP addresses of client and server

Timing of packets

Size of packets

Hostname via SNI

Part C — Making Sense of It
8. Why does the protocol choice (HTTP vs HTTPS) matter for confidentiality?
Because HTTP sends data in plaintext, while HTTPS encrypts all content and protects sensitive information.

9. Name one situation where you might send traffic over an untrusted network. What protects you, and what is still exposed?
Example: Using public Wi‑Fi

Protected: Content of communication (via HTTPS encryption)

Exposed: IP addresses, timing, packet sizes, hostname (SNI)

What surprised me most
The biggest surprise was how HTTP exposes everything — even the password — in readable text, while HTTPS hides all content in encrypted data. It was also surprising that the server name (SNI) is still visible in TLS.
