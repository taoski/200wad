---
title: "Check, Fart, Die"
created_at: 2020-08-14T23:26:51.000Z
published_at: 2020-08-15T00:20:22.000Z
---
I [wrote before](https://cowriters.app/words/idea-430355f15ba8e8f141) about creating a parody website where you could create a random UK Government "Get ready for Brexit" ad.  My idea was to make it totally random, creating images with random buzzwords on, in a similar style and layout.

I shelved the project because I got overwhelmed with thoughts about how and where I might host it, especially if it proved popular.

It popped back into my head last night as my wife was watching something on TV I wasn't enjoying.  So I grabbed my laptop and fired up Local by Flywheel for a quick and dirty PHP/Apache environment.

I have worked with the PHP GD image library code once before, many moons ago.  But I knew there would be something better or easier to use by now.

I found [Intervention Image](http://image.intervention.io/), a PHP library letting you quickly and easily create, resize and filter images, adding text on the fly too.  I had to install it via [composer](https://getcomposer.org/), which I have not used before either, so I was learning something new too.

Within an hour and with the help of a handful of images from Unsplash, I had my working prototype.

The PHP code chose an image at random from a folder, resized it to 800\*600px and lowered the brightness by 20%.

Then, it chose 3 random words from a preset list I created as an array.  Words like "Check", "Go", "Panic", "Cry", "Avoid", "Fart", "Lie" and "Export" were used.

The code then looped through the 3 words, positioning them as white text on the image in the lower left hand corner.  I had to fiddle a little with font sizes and spacing, but it wasn't too much hard work to place them one above the other.

The original poster also has red, orange and green check marks next to each word.  I found a [TrueType Font version of the Awesome Fonts icons](https://github.com/creationix/font-awesome/blob/master/FontAwesome.ttf) and added one next to each word, setting the right color too.  I also added some randomness to the icons, so instead of the standard check marks, you get things like question marks, warning triangles or skulls.

When you refresh the page, everything is created randomly on the fly.

So, what's next?

More words
----------

I want to add more text to the images.  The [original ads](https://www.newsworks.org.uk/creative-gallery/170256) have words like "UK'S NEW START" and "LET'S GET GOING" on them.  All ripe for adding something more sarcastic, again taken from a random list of options.

```
"IT'S DOWNHILL FROM HERE..."
```

```
"ABANDON HOPE"
```

Better and more images
----------------------

I then want to hand-pick some better images to use as the background.  The original adverts have people working, building, welding or making things.  I am sure I can have some fun with that too.

There are some excellent images of British politicians in compromising situations I can use, as well as a few very random things on British people will enjoy.

I also need to look at setting up each of the images better first, making them the right size and with the right filters or gradients applied already.  This will give the PHP code less to do, making it quicker.

That will be a job for Photoshop, or more accurately, my Son.

Sharing
-------

I then need to work out how to make it so someone can share the image on social media.  I worry that a link from Facebook to the site will just create a new image, rather than reload the shared one.  I might need to look at caching the images somehow or using some URL parameters to manually construct the image.

Rather than picking randomly from a list of words, if the URL was mydomain.com/?words=1,5,9&image=1&quote=2&icons=4,7,10 it could recreate the image based on those values.  Easy enough to do.

But then the URL looks shit.  I might have to work some .htaccess magic instead.

Fonts
-----

I would also like to use the same font as the ads, but it seems that it is [only licensed for use on UK Government websites](https://designnotes.blog.gov.uk/2015/03/11/can-i-use-the-gov-uk-fonts/).  However, I think I have found a suitable replacement already.
