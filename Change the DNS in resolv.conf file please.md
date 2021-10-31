Change the DNS in resolv.conf file please. 

1. Open Terminal application and use this command: sudo nano /etc/resolv.conf  It may ask user password, provide it. Typing in your password does not show in a terminal, just type in your password and hit enter. This is to stop anyone looking over your shoulder from seeing how many characters your password consists of. 
2. 2. Comment existing records using # symbol and add new DNS records like: nameserver x.x.x.x where x.x.x.x is your new DNS server.  For Google public DNS use 8.8.8.8 and 8.8.4.4 For StrongVPN you can use: 216.131.94.5 and 216.131.95.20  Use Ctrl+X to save file and Y to confirm all. 
   3.  3. Some Linux services can change DNS config files automatically, to prevent this we will lock the file. Use this command: sudo chattr +i /etc/resolv.conf  To unlock the file (if you want to change DNS again) you will need this command: sudo chattr -i /etc/resolv.conf

