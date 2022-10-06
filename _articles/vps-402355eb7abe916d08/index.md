---
title: "VPS"
created_at: 2020-05-10T16:23:21.000Z
published_at: 2020-05-10T16:31:52.000Z
---
Having to deal with your VPS server being down within minutes of you waking up definitely helps shock you into action.  I had to deal with this yesterday.

I have been recently instaling the Wordfence firewall plugin to all of my WordPress sites and regularly get emails telling me things need updating or checking.  Having an out of date or unused plugin or theme on WordPress is the perfect back door for hackers to get in and Wordfence tells you about them as they need updating or removing.  It is useful if a little overzealous.

I knew I had some alerts to deal with on a few of my sites, but also noticed that I had an alert from uptimerobot to say my server was temporarily offline.  No biggie, it happens from time to time.  But as I logged into my first WordPress site, it was crawling, so I connected to the VPS via SSH to see what was going on, which again was very slow.

After much digging using Linux commands to determine the problem, it turned out that my VPS had run out of disk space.  The log files from one of my non-WordPress sites were at over 26Gb and there were lots of backups of my websites taking up room.

So I deleted the backup folders and reset the setting to only store 1 backup at a time.  I then deleted the logs and had to restart the web services to allow the disk space to be properly freed up.

This whole "manage your own server" thing is cheap, but comes with a steep learning curve.  I now need to look into limiting the size of Apache log files, setting up some sort of alerting system and deal with the daily list of issues Wordfence throws up.  The latest is how I can send out email from contact forms on the WordPress sites, but so that they bypass any SPAM filters and arrive in the inbox.

All good fun?
