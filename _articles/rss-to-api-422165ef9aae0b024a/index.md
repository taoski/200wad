---
title: "RSS to API"
created_at: 2020-06-29T17:48:32.000Z
published_at: 2020-06-29T18:55:15.000Z
---
I managed to find time over the weekend to work on fixing the code on a WordPress plugin to work with the eBay Partner Network API.  In short, they announced at the beginning of June that their RSS generator, upon which many third party tools are built, would be decommissioned in 30 days time.  This left many affiliates panicking and with not much time to learn to code from scratch, they were a little miffed, to say the least!  The eBay Partner Network team then announced that the RSS feeds would still work until the end of August, giving people a little more time to convert to something new.

I use a third party plugin on a few of my websites, promoting antique type items through which I get payment from eBay if someone clicks and then buys something.  Over the years it has been a good source of additional income.

The plugin relies on the (now impendingly defunct) RSS feed to gather it's data, so it needed to be converted to use an API instead.

The main issue with this, is that the plugin code is obfuscated.  If you were too open it up in your favorite text editor, the majority of it is just gibberish and hexadecimal code.  Luckily, there are services, apps and websites that will deobfuscate the code for you, but you are then left with 50% PHP and HTML code, 50% compacted code (that needs to be run through a prettifier) and 90% unreadable variable or function names like:

```
$0v0nv08voweintvowt = n08nv04nbpt084ut__43rw();
```

However, I have managed to get it all working.

I added an additional function to convert the RSS URL parameters to the API and also added some additional fields to the plugin's admin page in WordPress.

There was one point in the migration where I managed to cause such a bad PHP crash that nothing was being written out to any logs, anywhere.  I ended up having to step through the code manually, adding a command to output something to the screen so I could see where I was and where it was stopping.

The error was related to a WordPress path variable not being populated correctly.  I was developing using Local by Flywheel, so its possible the local instance was causing the problem.  I will see when I make the code productive on one of my sites this week.

The question is, do I sell my fix?

There is definitely a hungry market out there for it... but I don't want to tread on the toes of the original developer.  However, he has since abandoned the plugin due to health issues.
