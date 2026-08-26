

In this lab, I first tried to fix the PC's IP address by requesting a new IP from the DHCP server. After getting the IP, I used ipconfig to check it and then used ping 64.100.1.1 to make sure the PC could connect to the HQ router.

After that, I tried to connect to the router using Telnet, but the connection was closed because Telnet was not allowed on the router.
 <img width="780" height="734" alt="image" src="https://github.com/user-attachments/assets/f3a191ca-c78e-4f90-9249-a6d9fe2fda3d" />

Then I used SSH with ssh -l admin 64.100.1.1 and entered the password class. The connection worked, and I was able to access the HQ router.
 
The final prompt was HQ>, which showed that I was successfully connected to the router using SSH.
<img width="780" height="734" alt="image" src="https://github.com/user-attachments/assets/f6c0fb84-dd37-40e4-9060-c2606cabfd61" />

