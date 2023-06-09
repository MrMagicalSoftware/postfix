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



# Dovecot


To install Dovecot on Ubuntu server, follow these steps:

    Update the package list:

    sudo apt update

    Install Dovecot and the necessary dependencies:

    sudo apt install dovecot-core dovecot-imapd dovecot-pop3d

    Stop the Dovecot service:

    sudo systemctl stop dovecot

    Edit the Dovecot configuration file:

    sudo nano /etc/dovecot/dovecot.conf

    Replace the contents of the file with the following:

    listen = *
    protocols = imap pop3 lmtp
    ssl = no
    disable_plaintext_auth = no
    mail_location = mbox:~/mail:INBOX=/var/mail/%u

    Save and exit the file.

    Edit the authentication configuration file:

    sudo nano /etc/dovecot/conf.d/10-auth.conf

    Uncomment the following lines:

    # Disable any methods that shouldn't be used for authentication.
    #auth_mechanisms = plain login

    Save and exit the file.

    Restart the Dovecot service:

    sudo systemctl start dovecot

That's it! You have successfully installed and configured Dovecot on your Ubuntu server.







