---
title: "Exim"
created_at: 2020-08-01T22:04:56.000Z
published_at: 2020-08-01T22:27:11.000Z
---
I wrote yesterday about the need to create a website for my son.

In the end, I opted to create a WordPress site, initially using Local by Flywheel on my MacBook which allowed me to use a local development environment.  I then exported the WordPress database, registered a domain and made the site live on my VPS.

Pretty easy stuff, apart from a few CSS tweaks here and there to realise his vision.

One of the things he wanted was a contact form on each page, where potential clients could reach out to him if they wanted him to work with them.  There are a shed-load of WordPress plugins for this, but seeing as I had installed the Coblocks plugin already, which adds some additional options when creating your posts and pages, I opted to use their offering.

After the site was finished from a visual perspective, I tested the form.

I never received the email.

Come to think of it, I haven’t had many emails from my websites over the last 5 days or so.  I usually get at least one, telling me I need to upgrade a theme or plugin to remain secure (thanks WordFence!).

I logged into my server using SSH and checked the services.  My Exim mail server was running and had been for over 50 days and nothing else looked amiss.  I had to dig a bit deeper, looking at the /var/log/exim/main.log file to see what was going on.

There were some errors where emails going to my gmail account were being blocked by Google.  They were no longer trusting that my server’s identity was correct.  So, off down the rabbit hole of adding more SPF and DMARC records I went.  Of course, messing with DNS is sometimes not an instant fix, so after going round in circles for a few hours, I changed the DNS nameserver records on his domain from the company I bought them from, to my VPS.  I shut my laptop and waited to look in the morning, hoping it would fix itself over night.

It didn’t.

I ran some tests from another contact form on another one of my websites, which still didn’t work.  I could see rejection and failure messages in the logs and it was clear there was something not quite right going on.

I found an online tool to help diagnose the issue - https://www.checktls.com/TestReceiver - which allowed me to query a domain, check the mail server records and then query that mail server, grabbing lots of information.  It turned out that the mail server’s HTTPS certificate was reporting as a generic “self signed” one, rather than one create specifically for that domain.

AgIan, off down the rabbit hole, trying to see where the Exim mail server software was getting it’s certificates from.  I found them, referenced in the configuration file, but then had to find out how to run an OpenSSL command to check if those had the same name as the self signed ones I could see from the CheckTLS site.

Bingo!

They were reporting as belonging to “example.domain.com” rather than “mail.twizzle.com”.

I updated the Exim configuration file to point at the correct certificates in the correct location, restarted a few services and low and behold, I was able to get the contact form on my son’s website to email my gmail account.

I am not sure why it stopped working.

Perhaps Google just imposed some tighter security, or perhaps some software on my server upgraded itself and overwrote the configuration file?  I can’t tell for sure.

I tested the contact form on another of my websites, but still didn’t receive any emails.  Damn.

Then, I realised that the email address it was being sent to was one belonging to the domain itself, not to my gmail account.  Some of the strange error messages I saw in the logs started to make more sense now.

\===

Of course, I am no Linux or server expert.  Running your own VPS means that you are scrabbling around on forums and websites, googling error messages and trying to tie back what you have found to your specific situation, software and setup.

I might have got the issue resolved, but it might come back again in the future.

However, the more I dig inside log files and use the command line to resolve issues, the more confident I become.  It reminds me of the (gold old) days of MS-DOS, editing autoexec.bat and config.sys to squeeze the best out of your system.

It’s nice to learn something new.  So, as frustrating as it was to find the fix, it was not a time-critical issue, so I could take my time and work through things properly.
