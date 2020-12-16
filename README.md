# Raspberry Pi as a Email server

# H1 In this Setup, you will learn how to build your Email Server on Raspberry PI

You will be using following Tools:

**Postfix**, open-source mail transfer agent that routes and delivers electronic mail.

**Dovecot**, open-source IMAP and POP3 server.

**MardiaDB** (MySQL), to store Email account details.

**RoundCube**, web-based IMAP email client to read and send your Emails.

# Read carefully

If you are setting up an Email server using your residential Internet connection you must check this:

## How to know if your Internet Service Providers(ISP) is blocking Email ports?
### This Tool nmap allo you to test it:
```shell
sudo apt-get install nmap
```
### run this command:
```shell
nmap -p 0-65535 portquiz.net > /tmp/nmaptest
```
### grep for the filtered ports like this:
```shell
grep filtered /tmp/nmaptest
```
### We need the port 25 to configure our own Email Server:
Create a **vmail** group and user a Home Directory.
```shell
sudo groupadd -g 5000 vmail 
sudo useradd -g vmail -u 5000 vmail -d /var/email -mt
```
### Configure IPTables Firewall
Add the following lines befor
```shell
# -------------- WEB

# -------------- MAIL
#SMTP
-A INPUT -p tcp --dport 25 -j ACCEPT
-A INPUT -p tcp --dport 465 -j ACCEPT
-A INPUT -p tcp --dport 587 -j ACCEPT
#IMAP(S)
-A INPUT -p tcp --dport 143 -j ACCEPT
-A INPUT -p tcp --dport 993 -j ACCEPT
#POP(S)
-A INPUT -p tcp --dport 110 -j ACCEPT
-A INPUT -p tcp --dport 995 -j ACCEPT
```
### Reload the IPTables rules
```shell
sudo iptables-restore < /etc/iptables.firewall.rules
```



