---
title: "EPN"
created_at: 2020-06-05T19:02:07.000Z
published_at: 2020-06-05T19:55:05.000Z
---
As some of you may remember from my previous writings, I own and manage a few website that make me some passive income.  They use either the Amazon or eBay affiliate program (the eBay Partner Network) to suggest products that, if you click through and buy, I get a small percentage of the sale back.

Part of working with systems like these is that, if you don't want to use the tools they provide to display the Amazon or eBay items, you can roll your own using their APIs or data feeds.  This means that you can create your own listings, styling them and presenting the information how you like, which usually increases the amount of times people click through to buy.

The issue there is when the interfaces change or in the case of an announcement this week from the eBay Partner Network, get totally decommissioned with less than 30 days notice.  They are ceasing their RSS interface at the end of June.  It's not even that this interface is not being used any longer - there are multiple tools and business built on this and it will leave a lot of people penniless.

Of course, part of playing this "make money online" game is that sometimes you get outsmarted by the other team and you have to quickly regroup, creating new attacks and defenses to win the game.  Or at least allow you to get near the goal again.

But in the case of eBay, the removal of this particular RSS interface means that you would have to switch to using their core API.  But that is limited to 5000 requests, per day!  Of course, you can request that this limit is raised to 1.5 million, but you need to be sending them some serious traffic and creating consistent sales for them to qualify.

It's not the first time this has happened.

eBay have even changed their interfaces without notice before, leaving people to scrabble to make quick changes in code they probably don't understand.  I made quite a bit of money from such a situation once, selling a tweak to and existing product that had been deserted by its owners.

Amazon also updated their API at the end of last year, requiring code rewrites or paid upgrades to existing tools.  It's all just par for the course.

So, where does this leave me and my websites now?

I have options to move to alternative affiliate programs, but some of my websites are based around antiques, so eBay is the best partner for those.  I could work on writing some code to use their API and either build in aggressive caching to guard against bots eating my quotas or add some sort of fall back ads if I hit that 1500 limit (or probably a combination of both).

Of course, there is the usual outrage on the eBay Partner Network forum and, as usual, answers from the staff there are not forthcoming.  It will be interesting to see how things progress in the next few weeks.

But it is a cautionary tale too.  Building your business upon other peoples tools can lead to issues like this.
