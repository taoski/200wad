---
title: "More Email Issues"
created_at: 2020-08-05T22:33:27.000Z
published_at: 2020-08-05T22:42:17.000Z
---
Issues with email on my VPS have come up again.

After setting up the website for my Son, he asked to have an email address set up, rather than use his (rather embarrassing) old GMail account for business stuff.

So, I added the account, sent a test mail to it and got an error

```
550 Relay not permitted
```

Ho hum.  Bugger.  Back to checking the configuration of the Exim mail server software I go.

I managed to bypass that error by adding the domain name to the configuration file somewhere, but then, when testing Exim against the new email address, I got a new error:

```
Lowest numbered MX record points to localhost
```

So, for some reason, the mail server thinks that a domain hosted on the same server is a remote domain.  It performs the DNS lookup, realizes that it is the same IP as the local server and stops.

Ho hum.  Bugger.  Back to checking the Exim config and logs.

I added the domain against another line in the Exim settings and emails now work ok.  I can see his mailbox has some messages in!

But.  I can't find a way of reading them.

I set up a mail client on my Son's phone to read the messages, but it won't connect.  Looks to be an SSL error with the mail alias not serving the correct certificate.  Either that, or the way I have configured the server is not correct.  I am getting confused if I should be using a centralized mail server address, or separate ones for each domain I have hosted on there.

I can't even log into the webmail to read his messages.  That also returns an error which I can't seem to fix.

I am just going round in circles, not quite knowing what I am doing.

I need to spend some time working out what is what and what goes where.  It would be great to look at a working configuration to see what I have done wrong.  I can post on a support forum, but I might not get a reply.  Perhaps Reddit might be a better place?
