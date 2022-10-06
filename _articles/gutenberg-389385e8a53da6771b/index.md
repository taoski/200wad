---
title: "Gutenberg"
created_at: 2020-04-06T06:55:38.000Z
published_at: 2020-04-06T07:07:35.000Z
---
Had a slowish day today, but was up early cleaning and putting the washing on.

I then started thinking of how I could tweak the core RSS Gutenberg block in WordPress to allow more options.  By default, you can set the RSS feed URL to import the list of items, show the publish date and an excerpt.  There is also ways to set the output as a list or in columns.

This is perfect for what I need to use as the base for creating a list of eBay auction items on my sites which I can get through their site.  At the moment, I use a paid WordPress plugin called phpBay, but the author has been sick for a while now and the plugin is no longer in development.  So, having a nice "block" in the WordPress editor would be a good thing.  Perhaps something I could also sell!

But the problem is, I have never made a Gutenberg block before.  I don't know any React.js and because the existing RSS block is built into WordPress, I can't seem to extract the code to convert it to become a plugin.  It won't be an issue adding the additional options I need, I just need to convert the core block to be a standalone plugin.

I spent more hours than I should have on this today.  To be honest, I was coding by the seat of my pants, making it up as I went along, checking blogs, Stack Overflow, comparing my code against other plugins and hoping things would work - which they didn't.  I think I might have worn out my CTRL+C and CTRL+V keys!

I found an old Gutenberg RSS block plugin (made a few years ago before it was added as a standard block).   It does work, despite not being updated for a long time, but lacks some of the editing/previewing bells and whistles the core block has.

So tomorrow, I plan to try to merge the two together.

I suspect it won't work, but I can try!

Meanwhile, I have left a query on Stack Overflow asking if anyone knows how to convert the core block to a plugin.  It has not been answered yet, which probably means it won't be.
