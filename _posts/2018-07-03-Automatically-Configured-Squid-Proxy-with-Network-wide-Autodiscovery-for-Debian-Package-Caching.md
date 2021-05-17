---
layout: post
title: Automatically configured Squid proxy with network-wide autodiscovery for Debian package caching
category: IT
tags: Debian Network Squid Avahi
---

In the past I used a manually configured Squid3 as a package cache. Recently that had to be
migrated to a new host and I after not touching that setup for maybe a decade, I wanted
to examine the squid config as a whole at first.
After seeing what a time consuming endeavour that would have been, I luckily stumbled upon the **squid-deb-proxy** and **squid-deb-proxy-client** packages.
And I confess: I rather lazily trust that, than reread over the **loooong** list of squid parameters.
While I'm sceptical about infrastructure depending to much on automagical configuration (in this case **avahi-daemon**) using these packages allowed the replacement within a few minutes.
On top of that, the packages usually don't interfere with any squid already in place (seperate instance and port).

On the host serving the cache (here **squid**):
~~~terminal
apt install squid-deb-proxy
~~~
Then collect and add all domains any client connects to below /etc/squid-deb-proxy/mirror-dstdomain.acl.d/
Either in the file already present or even better in seperate files
(e.g., 20-cran-rproject, 30-postgres-upstream, 40-grnet)

On the clients it's enough to
~~~terminal
apt install squid-deb-proxy-client
~~~

After adding the necessary firewall rules for squid on the server it's time for a testdrive.
Suddenly missing **Release** files are a sign that the domain didn't make it into the ACL directory.
If no unusual warnings and errors appear squid:/var/cache/squid-deb-proxy/ should show the typical directory tree filling up:
~~~terminal
squid:/var/cache/squid-deb-proxy# tree -L 1
.
├── 00
├── 01
├── 02
...
├── 0F
└── swap.state
~~~

Sofar that worked like a charm and IMO cannot be much easier.
