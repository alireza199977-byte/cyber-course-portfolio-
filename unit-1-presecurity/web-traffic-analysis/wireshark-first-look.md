**1. Find the login submission. What username and password were sent? Paste the line from the stream where you found them.**

POST /login HTTP/1.1
username=testuser&password=SuperSecret123
---
**2 . The login form was submitted using which HTTP method — GET or POST? (Look at the packet that carries the credentials.)**

POST
The credentials are inside the HTTP body, not the URL.
---
**3. After a successful login, the server sends back a Set-Cookie header. What is the value of the SESSIONID cookie? Why might an attacker who sees this cookie be dangerous, even without the password?**

Set-Cookie: SESSIONID=abc123xyz789; Path=/; HttpOnly
Why dangerous?  
If an attacker steals this cookie, they can hijack the session and log in as the user without needing the password.
---
**4. The dashboard page (the final server response) reveals personal details about the user. List two pieces of sensitive information visible there.**

Full name of the user
Email address / employee ID / personal profile details
---
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
