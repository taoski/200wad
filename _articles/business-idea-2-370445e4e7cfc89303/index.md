---
title: "Business Idea #2"
created_at: 2020-02-20T20:35:08.000Z
published_at: 2020-02-20T22:11:59.000Z
---
This is more of an idea for an app/service than a business.

**The background:**

I noticed that both my colleague and I take daily notes and store them in Notepad files on our laptops.  They contain small notes that I take when on the phone to people, or whilst I am working.  These notes could be a list of things I need to remember to do, IP addresses or servers I need to fix or phone numbers of people I need to call back.  It varies from day to day.

On the off-chance that I reboot my laptop, I save the file with today's date just in case I need to reference it later.  However, my colleague always saves a file each day, starting anew each time.

But it can be hard to find old information, especially if I can't remember what day it was recorded on.  Also, what happened to my todo list from a few days ago that I forgot to complete or where my laptop crashed and I lost it all?

Surely there must be a better way to do this and make it better.

**The idea:**

A web app that automatically creates a new notes page per day as you sign in.

Any old notes that contain a todo list with uncompleted items are brought forward to that new day.  Other old items can be marked to be carried over to the new day too.

The information is all searchable and old notes can be edited and items carried through to the current notes page if needed.  Images can also be pasted in too.

It kind of works similar to how a [bullet journal](https://bulletjournal.com/pages/learn) works.  Information is logged quickly but can be reviewed and brought forward.

**The implementation:**

The app would need to rely on a database to store the information per user.  It should also autosave the data as it is written.

A job should run as a new page is created to import older items that are to be "carried forward" such as notes or todo lists.  This job should also run periodically in case an old note is edited and the information need to be carried forward.

The "carry forward" could be as simple as adding a ">" to the beginning of the line.  As per the bullet journal method, being able to log tasks and notes quickly will be helpful, so assigning bullets or characters should be quick and simple.

**How it makes money:**

It would be nice to start with a very basic daily note taking system and then add additional features that could be sold as part of a premium version.  It would be a monthly subscription model.

**MVP:**

Create a basic framework to allow individual user login, automatic note creation if the date has changed from the last login/refresh.  Work on a good UI to allow quick searching of notes or moving between different days.
