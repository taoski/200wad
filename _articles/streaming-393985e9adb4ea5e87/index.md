---
title: "Streaming"
created_at: 2020-04-18T19:49:50.000Z
published_at: 2020-04-18T20:08:17.000Z
---
Yesterday, my son hosted a listening party on Twitter for his favorite band.  He had spent weeks creating his own music videos for each song and a set list (based on a real gig set list).  In the end, he landed with a 1.5 hours long, 3.5 gigabyte video, resized to 480p to keep the file size down.  The idea being that having the file previously shared and downloaded days before, everyone would start to watch at 6 PM and enjoy their own "virtual concert" at home.

Of course, this was all without the say so of the band themselves and sharing a hosting a video containing their audio leads to possible piracy issues.  Initially, the  video was shared to 2 separate Google Drive accounts.  However, even Google Drive limits the daily download of files, so despite sharing it early, people were still getting locked out.  I then agreed to host the file on one of my websites for people to download.

However, my website was not so happy come 6 PM.  Luckily, it was hosted on a VPS, but I kept getting emails from [uptimerobot](https://uptimerobot.com/) telling me the site was down, messages about services crashing and memory being exceeded.  He is not sure how many people were able to view the video, but it did seem like people were trying to stream it direct from my site rather than downloading the file first as instructed.

The problem, we found, is that depending on the device you are using to access the file, it will either prompt to download it to your device, or start to stream it.  My Google Pixel phone wanted to download it, but anything Apple related tried to play the file direct.  Probably browser specific too.

I checked my traffic stats on the VPS this morning and over 1.5TB of data was served yesterday.  I suspect I will be getting a bill for that extra bandwidth next month.

In the days leading up to the party, we were looking at ways to host the video.  YouTube is not an option as the video would be copyright claimed and banned almost immediately.  Other less politically correct sites like DailyMotion or LiveLeak would not allow him to upload the video as it was too large for a free account.  Twitch or Vimeo would also probably strike the video down too, so we didn't even try there.

Perhaps the best way would have been to create a torrent of the video and direct people to a website where the video could be streamed using a magnet link (eg: webtor.io) , not downloaded.  Not ideal, but it might have been a good solution when there were (an estimated) 400 people watching at once.  The larger the number of people streaming, the better and quicker the torrent stream would be.

It also proves how much data YouTube must get through each day, even for just one popular video.  I know they are able to transcode each video to better, quicker formats or play ones applicable to the device you are using, but sheesh, I can't imagine how much bandwidth an HD or 4K video uses.

Obviously, we wanted to steer clear of any legal issues (all hosted videos have been removed) but I wish there was a better, more stable way to do more transient shares or events like this.
