---
layout: post
title: Delete all files excluding some by pattern
category: IT
tags: Linux Storage CLI
---

Reminder to myself: find has negation to parameters
~~~terminal
find . -type f ! -name '*.tar.gz' -delete
~~~

or if it's a find implementation without "delete":
~~~terminal
find . -type f ! -name "*.tar.gz" -exec rm -rf {} \;
~~~
