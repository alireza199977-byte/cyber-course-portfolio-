
I connected three PCs (PC0, PC1, and PC2) to the wireless router using straight-through cables.
First, I checked the default gateway, which was:
192.168.1.1
Then I changed the router IP address to:
192.168.5.1
I also changed the DHCP settings:
•	Start IP: 192.168.5.126
•	Maximum Users: 75
After enabling DHCP on all PCs, they received these IP addresses:
•	PC0 → 192.168.5.126
•	PC1 → 192.168.5.127
•	PC2 → 192.168.5.128
Finally, I used ping from PC2 to check the router, PC0, and PC1. All connections worked successfully.
