---
title: "eMailz"
created_at: 2020-08-10T03:09:46.000Z
published_at: 2020-08-10T03:14:33.000Z
---
I have still been trying to get to the bottom of the email issue on my VPS server.

I have managed to get past the local error where it performs a DNS lookup for the domain, rather than realising it is a local one.  Emails seem to be passing through to the mailbox, but when I log in, there are no messages to be seen.

Strangely, when I look at the users mailbox in the VestaCP admin page, it shows as being 1Mb in size, so there does appear to be something there.

There is one option.

When I first set up the account, I added it as an additional mailbox on my son’s iPhone.  Perhaps the messages are all going there?

The next steps will be for me to find out where the messages are physically stored for his domain and put a “watch” command on the directory.  I can the run a test and see if things change and files are added, moved or deleted.

I am still learning stuff as I go though, finding new ways of doing things and new commands to run.  I need to start keeping a list of them.  I have forgotten quite a few already that I think will be important.
