---
title: "Emails"
created_at: 2020-08-11T15:59:19.000Z
published_at: 2020-08-11T16:31:44.000Z
---
I think I might have fixed the email issue on my VPS.

I spent several hours last night reading up on various error messages, trying to work out what was wrong.  It was hot here in the UK, so I was sweating my way through log files and testing IMAP connections via TELNET until 11:30 PM.

But, I think I might have cracked it, or at least made good headway.

There are several components at play here.

1.  VestaCP - the free web panel that I use to manage my VPS.  Here, I can create domains, users, databases, mail accounts etc.
2.  Exim - the free mail server program, used to process emails in and out of my VPS.
3.  Dovecot - a free IMAP and POP3 service, allowing people to send emails to my VPS users and for me to log in to access them.
4.  Roundcube - a free webmail software (which I didn't plan to use).

Firstly, I realised that when testing the other day, in VestaCP I had set the test account to automatically forward all emails to my Gmail account.  This might account for some of the odd messages I was seeing in the Exim logs, where Google was rejecting emails based on SPAM rules.  I had assumed the emails were from another source/account.

Mails were being delivered and processed by Exim for my test user, but I couldn't see where they were going.  All log files were saying it had been processed via "local\_delivery", but when I connected via IMAP, the folders were empty.

It turned out that the emails were being sent to the UNIX default location, which is /var/mail/username where username is a just a flat file containing the email data.

There is a configuration setting in the Dovecot /etc/dovecot/conf.d/10-mail.conf file that says where the emails should be placed upon receipt:

```
mail_location = maildir:%h/mail/%d/%n
```

%h meaning "path to the users home folder" %d meaning "domain" and %n meaning user

So the emails should be put in a folder like this:

```
/home/testuser/mail/domain.com/testuser
```

I found the folder.  The structure was there, showing inbox, drafts etc, but they were all empty.

Although the various components of Exim and Dovecot were set up automagically for me when I installed VestaCP, I suspected something wasn't quite right.  There was nothing in the Exim configuration file that referenced Dovecot, but I wasn't convinced there should be either.  But everything was running ok, just in isolation of each other.

I decided to backtrack and manually configure them myself.

I found an excellent tutorial on [installing a mail server with Exim and Dovecot](https://www.rosehosting.com/blog/setup-a-mailserver-with-exim-and-dovecot-on-a-centos-7-vps/) and followed their configuration to the letter (apart from the initial installation parts).

Seems that there was definitely some things missing from my Exim configuration.  The emails were not being processed by the Dovecot services at all, so no wonder I couldn't see them when I logged in.

I restarted the services, sent a few test mails and prayed to the email gods.

```
telnet mydomain.com 143
```

```
Connected to mydomain.com.
Escape character is '^]'.
```

```
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN AUTH=LOGIN] Dovecot ready.
```

```
. LOGIN testuser@mydomain.com mydomain123!
```

```
. OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE SORT SORT=DISPLAY THREAD=REFERENCES THREAD=REFS THREAD=ORDEREDSUBJECT MULTIAPPEND URL-PARTIAL CATENATE UNSELECT CHILDREN NAMESPACE UIDPLUS LIST-EXTENDED I18NLEVEL=1 CONDSTORE QRESYNC ESEARCH ESORT SEARCHRES WITHIN CONTEXT=SEARCH LIST-STATUS BINARY MOVE SNIPPET=FUZZY SPECIAL-USE] Logged in
```

```
. LIST "" * RETURN (STATUS (MESSAGES))
* LIST () "." Sent
* STATUS Sent (MESSAGES 0)
* LIST () "." Trash
* STATUS Trash (MESSAGES 0)
* LIST () "." Junk
* STATUS Junk (MESSAGES 0)
* LIST () "." Drafts
* STATUS Drafts (MESSAGES 0)
* LIST () "." INBOX
* STATUS INBOX (MESSAGES 3)
. OK List completed (0.003 + 0.000 + 0.003 secs).
```

3 MESSAGES IN THE INBOX!  Whoooooo!

I went to bed and dreamed a mangled combination of POP3, SMTP and IMAP things.

Now, I just need to get the email client working on my Son's iPhone.

That could be a whole other confusing mess of SSL certificate problems.
