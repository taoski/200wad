---
title: "Self Managed"
created_at: 2020-04-25T20:45:27.000Z
published_at: 2020-04-25T20:54:54.000Z
---
The self-managed part of my new VPS has already started to show its face.

As I was getting to know my way around, adding new domains and setting up new services ready to test a transfer of one of my domains, I came across an issue.

I was not able to resolve any hostnames.  I was not even able to ping google.com but could ping IP addresses ok.

Using the little knowledge of the NAMED DNS service, I started to research and look into the issue.  I added different DNS server IP addresses, checked and rechecked the configuration but it was all to no avail.  No matter what, I was not able to connect out.

So I logged a ticket to the provider asking for assistance.

Their reply was pretty scant to be fair.  They asked me to do a few things I had already tried and also pointed me to a few forum posts, suggesting I had installed something that might be causing the issue.

In the end, I gave them permission to reboot the server to a recovery mode and test.  They came back pretty quick with a screenshot showing them being able to resolve google.com to an IP address ok, so it must have been something I had done that was causing the issue.

But all I had done was log into the web panel of the VPS and start trying to add a domain or two.  I had hardly been in the console before this happened.

In the end I found that the default firewall configuration on the VPS was blocking outgoing DNS queries.  I managed to find some additional entries to add to my IPTABLES firewall configuration file which fixed it.

I get that it is “self managed” but I did expect the VPS to be set up in such a way that I could just start using it without too much hassle.  Perhaps I misunderstood exactly what I was getting myself into.

I now have another issue I am investigating because I can’t apply a LetsEncrypt free SSL certificate to the primary domain.  I suspect this is because the VPS has both an internal and public IP with a NAT between the two.  When the domain is trying to be registered with LetsEncrypt, it is showing the wrong IP address.

Anyway, at least I am learning stuff!
