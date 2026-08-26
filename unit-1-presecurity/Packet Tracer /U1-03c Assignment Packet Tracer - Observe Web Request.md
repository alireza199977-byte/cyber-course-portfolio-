
I checked how a PC communicates with a web server in Packet Tracer. First, I used ping ciscolearn.web.com to test the connection and see the server's IP address.

  <img width="490" height="662" alt="image" src="https://github.com/user-attachments/assets/c6b3cf94-37c5-42b9-802d-ac83ec025a22" />


Then, I opened ciscolearn.web.com in the web browser and checked the index.html file on the server to see the HTML code of the web page.


After that, I switched to Simulation Mode and created a Complex PDU using HTTP. I set the source as External Client, the destination as ciscolearn.web.com, the source port to 1000, and the interval to 120 seconds.

 <img width="490" height="662" alt="image" src="https://github.com/user-attachments/assets/e42dc031-70c8-47f6-9527-97524ce283de" />


Finally, I played the simulation and observed the TCP and HTTP packets moving between the client and the web server. This helped me understand how TCP and HTTP work together when a client requests a web page.


