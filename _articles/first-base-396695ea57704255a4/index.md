---
title: "First Base"
created_at: 2020-04-26T20:56:52.000Z
published_at: 2020-04-26T21:06:30.000Z
---
Success!

I managed to transfer a website from my old VPS to the new one this morning.

The new VPS was preinstalled with the Vesta Contol Panel, NGINX web server, PHP-FPM and CENTOS 7.  My previous VPS was CENTOS 7, WHM, cPanel, Apache and standard PHP - so just a little enough change to make things interesting.

In the end, I deleted the Vesta control panel, NGINX and PHP-FPM and reinstalled in favour of Vesta, Apache and PHP.  Back to something similar to what I was used to.  It also helped me see the wood from the trees more, knowing which log files to look in and how to tweak some additional settings.

Being a PC user from the (good ol') DOS days, it is kinda nice getting to know the command line of your server rather than relying on a GUI all the time.  Thank goodness Google is there to help me too.  I know what I want to achieve, just not exactly how or where to achieve it.

So my next steps will be to start transferring my other Wordpress sites over one-by-one.  They each have slightly different requirements, plugins or scripts that I will need to ensure still work in the new environment.  Some sites are larger than others, so I will need to ensure I delete cache files before I ZIP up the folders.  Alternatively, I might be able to copy everything directly from one VPS to the other using RSYNC, which I have not used before.

I am feeling much happier about the new VPS purchase now.  We are over the initial flirting period and I have gotten to first base.  I was feeling a bit despondent at first, thinking I would have to go back to the provider, asking for more help.  Once the sites have been transferred, I will need to consider hardening the server and monitoring to ensure everything is running as expected.

More fun and games.
