---
layout: post
title: Using wget with HTTP 
category: IT
tags: Linux Network CLI quirks
---

Reminder to myself: wget supports globbing with FTP, but wants "acceptance" and "rejection"-lists for HTTP(S).
Excerpt from the wget(1) man page: 
> -A acclist --accept acclist
> -R rejlist --reject rejlist
>     Specify comma-separated lists of file name suffixes or patterns to
>     accept or reject. Note that if any of the wildcard characters, *, ?,
>     [ or ], appear in an element of acclist or rejlist, it will be
>     treated as a pattern, rather than a suffix.  In this case, you have
>     to enclose the pattern into quotes to prevent your shell from
>     expanding it, like in -A "*.mp3" or -A '*.mp3'.

Thus some old download via FTP like
~~~terminal
wget -c -r -N -nH -nd ftp://example.net/pmc/articles*.xml.tar.gz 1>> /var/log/pmc_updates.log 2>> /var/log/pmc_updates.err
~~~
becomes someting close to
~~~terminal
wget -c -r -N -nH -nd --accept 'articles*.xml.tar.gz' --https-only https://example.net/pmc/ 1>> /var/log/pmc_updates.log 2>> /var/log/pmc_updates.err
~~~

Would be to easy to just change the protocol in old scripts... *gnargh*
