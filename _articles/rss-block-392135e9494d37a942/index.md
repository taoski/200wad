---
title: "RSS Block"
created_at: 2020-04-14T01:35:31.000Z
published_at: 2020-04-14T02:56:01.000Z
---
I have given up trying to change the Wordpress Gutenberg RSS block into a stand-alone plugin so I can tweak it to show eBay items.

Trying to reverse engineer code that you hardly understand is hard work.  It is also the first time I have messed with React.js too, so a double whammy.

Instead, I will start by taking some example custom Gutenberg block code and then adding my own PHP code around it.  I found something applicable earlier which should work ok.

One main thing I am looking for is the ability to be able to update the block settings and then have the changes render ”server side” on the fly.  This, compared to making a setting change, saving your post and previewing the new post, will be a game-changer.  The example plugin code I have allows for this to happen automatically, so I just need to remove the example code and add in my own code to fetch the RSS feed and slice it accordingly.

I will also be looking to offer different layouts of the output too.  The core RSS block has the ability to split the feed items into columns, which is good, so I will probably steal how that works.
