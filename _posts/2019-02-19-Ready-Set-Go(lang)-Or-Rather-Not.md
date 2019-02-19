---
layout: post
title: Ready, Set, Golang, Or Rather Not
category: IT
tags: Golang Rant
---

In the past I started introductionary courses for Golang and honestly gave up really quick because the documentation _never_ matched the reality.
Now nearly a decade has gone by and Golang is still a construction site.

If you hate ranting, don't read any further.

From here on my experience during the "Introduction to Go" learning path from O'Reilly
-- correct me if I'm wrong. Either via Disqus comments or via the e-Mail-address provide on the "about" page.

Take for example the current official documentation for Golang 1.11 (current stable).
You should be able to "go get golang.org/x/tour tour" [sic!] and magically a browser windows opens
-- even the web-based Go tour says so.
 
Problem(s) are -- yupp, there are multiple problems right from the start:

1. there seems to be a typo. The second "tour" is not correct and will lead to an error message right from the start.

2. the issue tracker is _full_ of _different_ advices _from project members_ how to fix that.
One reason being, that they seem to change that from version to version.
Let that sink in a little, a programming language community that has more than a decade of history
isn't able to provide a correct instructions to their most important tutorial?

3. One advice is to set the environment variable "GOPATH" or "GOROOT" -- quickly forget that, it's _not_ the problem.
Let's think about debugging environment variables. First try, failure. echo $GOPATH won't help us, because that's empty, 
maybe randomly reading through all the go commands will help and luckily find something about "The Go environment" via "go env" 
-- why isn't that right on the starter page? Well, doesn't sell well, that one has to jump through hoops with Golang like with 
a lot of other languages...
At least we can see in the output of "go env", additinal to a lot of other variables, GOPATH is set to ~/go automatically 
if GOPATH isn't set (by your shell configs).
And people are complaining about systemd setting things without anybody knowing? Or maven's convention over configuration?
Anyway, looking into ~/go (e.g. with the "tree" command) will also reveal the results of failed "go get".
The sources of the Go tour were silently downloaded... so long, and thanks for all the fish!

4. you have to "go build" that package to get a binary. Does the tutorial mention that? Sure bet: nope.

5. you have to explicitly start that binary and only than will there be a Go tour for the very beginner. 
A Makefile would have been to easy I guess.

That. Is. An. Insane. Steaming. Pile. Of. Shit. -- but not a good start for a beginner.

Anyway, I'm still motivated enough to wade through the Golang sewage. Can't be much worse, or can it?
