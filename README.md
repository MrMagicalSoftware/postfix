# postfix


sudo -s

adduser demo

usermod -aG sudo demo

sudo hostnamectl set-hostname nomeDelDominio.com


#Aggiunta dei record DNS


RECORD 
TYPE A  name : nomeDelDominio.com IPadress : ipdelserver
TYPE A  name : mail    IPadress : ipdelserver
TYPE MX name : nomeDelDominio.com    MailServer: mail.nomeDelDominio.com


#Installazione di Postfix :

sudo apt-get install postfix


System mail name :

nomeDelDominio.com

sudo systemctl status postfix

sudo dpkg-reconfigure postfix

![Schermata 2023-04-04 alle 14 22 41](https://user-images.githubusercontent.com/98833112/229790186-6dede353-1f9a-49f0-81b8-a1ccfb4985f2.png)


![Schermata 2023-04-04 alle 14 23 12](https://user-images.githubusercontent.com/98833112/229790299-46951197-f967-4774-a73c-6f22a85a960f.png)


![Schermata 2023-04-04 alle 14 23 12](https://user-images.githubusercontent.com/98833112/229790442-71f480cb-234b-49a2-9d55-b2662b0b66d6.png)


apt install mailutils



Test email server :

/usr/sbin/sendmail ricevente@gmail.com (press enter)
test send mail

Press ctrl d  to send


How to prevent spam folder :

sudo nano /etc/postfix/main.cf

Add this line :

home_mailbox = Maildir/

or run : sudo postconf -e 'home_mailbox= Maildir\'

_________----------------------------------_______________


DOVECOT

_________________________________________________________

Fonte : https://www.youtube.com/watch?v=P5NeyiRPYiY&t=68s

sudo apt-get install dovecot-imapd dovecot-pop3d
sudo systemctl restart dovecot
nano /etc/dovecot/dovecot.conf
add this line :

portocols = pop3 pop3s imap imaps

____________________________________________

port di imap : 995











