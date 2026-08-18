**1. Find the login submission. What username and password were sent? Paste the line from the stream.**

POST /login HTTP/1.1
username=anna.virtanen&password=Summer2026!&remember=on

**2. The login form was submitted using which HTTP method — GET or POST?**
POST  
The credentials appear in the HTTP request body, which means the form used POST.

**3. After a successful login, what is the value of the SESSIONID cookie? Why might an attacker who sees this cookie be dangerous?**

Set-Cookie: SESSIONID=a3f9c2e7b81d4f60a5e2c9d10f4b7e88; Path=/; HttpOnly
Why dangerous?  
If an attacker obtains this cookie, they can hijack the user’s session and access the account without knowing the password.

**4. The dashboard page reveals personal details. List two pieces of sensitive information visible there.**
Full name: Anna Virtanen

Email: anna.virtanen@pohjola-logistics.local

**5. Apply the filter tls. Can you find the username and password anywhere in this capture? Why or why not?**  

**No**

....N...J......l%..k=.P...@....'..e..
........./.0.................lab-portal.local
....*...&......!}
3..(.:..)......G.....T.<.../.....K...G..D..A0..=0..%.......w.M...sj.......(!a
---
**6. Look at the first TLS packet (the "Client Hello"). One piece of plaintext is still visible here: the name of the server the client is connecting to. What is it? (Hint: look for "Server Name" / SNI in the packet details.)**

lab-portal.local
This is one of the few plaintext fields in TLS.
---
**7. Even though the contents are encrypted, name one thing an eavesdropper can still learn from the HTTPS capture (think about addresses, timing, or sizes).**

An attacker can still see:
IP addresses of client and server
Timing of packets
Size of packets
The hostname via SNI
---
**8. In one sentence: why does the protocol choice (HTTP vs HTTPS) matter for confidentiality?**

Because HTTP sends all data in plaintext, while HTTPS encrypts all content, preventing attackers from reading credentials or sensitive information.
---
**9. Name one situation in your daily life where you might be sending traffic over an untrusted network (e.g. public Wi-Fi). What protects you, and what would still be exposed?**

HTTPS protects the content of your communication by encrypting it
But IP addresses, timing, packet sizes, and the hostname (via SNI) are still visible 

---


**What surprised me most
The biggest surprise was how HTTP exposes everything — even the password — in readable text, while HTTPS hides all content in encrypted data. It was also surprising that the server name (SNI) is still visible in TLS.**
