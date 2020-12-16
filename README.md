# Raspberry Pi as a Email server

# H1 In this Setup, you will learn how to build your Email Server on Raspberry PI

You will be using following Tools:

**Postfix**, open-source mail transfer agent that routes and delivers electronic mail.

**Dovecot**, open-source IMAP and POP3 server.

**MardiaDB** (MySQL), to store Email account details.

**RoundCube**, web-based IMAP email client to read and send your Emails.

# H1 Read carefully

If you are setting up an Email server using your residential Internet connection you must check this:

## H2 How to know if your Internet Service Providers(ISP) is blocking Email ports?
### H3 This Tool nmap allo you to test it:
```shell
sudo apt-get install nmap
```
### H3 run this command:
```shell
nmap -p 0-65535 portquiz.net > /tmp/nmaptest
```
### H3 grep for the filtered ports like this:
