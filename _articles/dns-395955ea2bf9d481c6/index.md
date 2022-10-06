---
title: "DNS"
created_at: 2020-04-24T19:29:49.000Z
published_at: 2020-04-24T19:38:00.000Z
---
My new VPS server is up and running now.

I registered a new generic domain to use for the server as I did with my previous one.  My idea is to migrate my existing sites one by one and then update their NS nameserver records to point to the new VPS.

I can temporarily access the new sites as I am working on them by adding them to my hosts file

```
1.2.3.4   mydomain.com www.mydomain.com
```

Of course, getting to know my way around a new VPS and Vesta control panel has not been easy and I have run into an issue already.  I can't resolve any external hostnames via DNS.

The VPS provider assigns the IP address settings to the server via DHCP, so their local DNS servers are preset.  I thought it might be because my new domain name has not propagated down to theirs, but I can't even resolve to google.com.

```
[root@localhost ~]# ping google.com
ping: google.com: Name or service not known
```

Or:

```
[root@localhost ~]# nslookup google.com
;; connection timed out; no servers could be reached
```

I have worked my way through various configuration files, network settings, resolver settings and tests but have drawn a blank.  I also compared the settings against the other VPS I have and it all seems to be similar.

I went with my tail between my legs and logged a ticket to their support team.

I don't mind getting my hands dirty in the config files, but the setup they provide is quite bare bones, without much system level logging turned on even.

It's hard to see the wood from the trees sometimes with things like this.
