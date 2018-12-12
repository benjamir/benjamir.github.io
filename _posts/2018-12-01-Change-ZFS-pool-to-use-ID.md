---
layout: post
title: Change ZFS pool to use disk identified by ID
category: IT
tags: Linux Storage ZFS
---

While not recommended, I use a ZFS on Linux in combination with an external USB drive.

One of these drives was setup before I knew about the issues arising from stand-by/disconnet 
during usage of a ZFS pool that has a path with the old drive schema (sda, sdb, ...) instead of
the recommended identification by ID.

A pool affected by such an event goes into **state: SUSPENDED** instead of **ONLINE** and the easiest fix in that case is a reboot 
&mdash; there is a way to move the path and (re-)import the pool, but I would recommend that only as a last resort,
if you're unable to fix the setup completly. If you're so desperate you'll find several *gists* on your own. 

To mitigate the issue, the pool can be changed to use the disk identified by ID:
~~~terminal
zpool export pool
zpool import -d /dev/disk/by-id pool
~~~

Check the pool's path with zpool status -v or zdb afterwards.
