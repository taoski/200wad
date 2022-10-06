---
title: "Wordfence"
created_at: 2020-05-18T17:13:41.000Z
published_at: 2020-05-18T18:05:13.000Z
---
Since moving my handful of WordPress sites to a new VPS server, I have installed the (free) Wordfence plugin on to each one.  Whilst my old VPS was self-managed, there already seemed to be a moderate amount of security built in already, so getting hacked was not looming on my radar at any time.

But it is surprising what Wordfence discovers.

I am using Wordfence Central, where I can monitor and scan all of my sites from one dashboard.  From there, I get email alerts telling me when WordPress plugins need updating, if there have been any admin logins to any of my sites, if there are unusual files found or instances of malware.

Considering I had migrated the sites "as is" from my old VPS, there were some oddities Wordfence found during its first few scans.

There were numerous copies of index.php (called index.php.bak) sitting in multiple WordPress folders on multiple sites.  There are usually blank index.php files there to prevent people from browsing the folders directly.  The "bak files" were not infected, but obviously a carry over from a failed update at some point.  I used a Linux command to find and delete all of the index.php.bak files across the /home directory on the VPS, rather than seeking out each one in turn and deleting them by hand.

Wordfence also found some PHP files that had been infected!  I used to have a newsletter plugin on one of my sites, which [was compromised a long time ago](https://www.wordfence.com/blog/2016/10/revslider-mailpoet-gravityforms-exploits-bypass-cloudflare-waf/).  I didn't have the plugin active, or even installed any longer, but there were files left behind that contained dodgy Base64 PHP code (usually a good sign you have been hacked).  Luckily, nothing had come of it though despite being possibly infected in 2016!

Yesterday, Wordfence alerted me to an IP address that had been blocked from logging in to one of my sites.  It had attempted and failed to do so 20 times and was duly blocked for being naughty.

I already have [an additional HTTP Authentication security layer](https://blogvault.net/password-protecting-wp-login-php-with-http-authentication/) on my /wp-login.php file where the browser will ask for an additional username and password before allowing you to access that file.  But somehow that was being bypassed by the potential hacker.  Out of interest, I made note of the IP address and delved into the Apache logs for the site in question.

The attacker was attempting to perform a brute force login to my site via /xmlrpc.php, an API interface to WordPress that allows external apps to interact with the site via sending XML messages, providing they have the right credentials.  I started going down the rabbit hole of how hackers were probing access possibilities via this API, but it still requires an admin username and password to the site to cause any damage.

WordPress also makes things easier for hackers by allowing you to query data about the site via the built in REST API.  You can extract quite a lot of data about a WordPress site by using this interface.

For example, if you know of a WordPress site, simply add "/wp-json/wp/v2/users" to the URL and (if it is not protected) you will see a list of all of the users on the site, their names and details.  It gives you a list of usernames to attempt to hack, on a plate!

I don't use any external apps via the /xmlrpc.php file (such as the WordPress app on my phone) so I also added it to the Apache configuration to be blocked, also asking for an additional username and password to be accessed.  Hopefully, this will keep the hackers out for now.  Luckily, enabling the Wordfence plugin blocks access to the REST API for specific queries unless you are already logged in.  Bonus!

Using WordPress puts a large target on your back and you need to be constantly updating your plugins, deleting things you are not using and protecting your back doors.  I don't mind doing this as I see it all as a learning experience, but I can also see the benefits of a simple, static HTML and CSS site too.  In fact, using a WordPress plugin to dump out a static site if you don't rely on any server side scripting or interactivity is worth it!
