---
layout: post
title: Increase padding of Gnome-Terminal
category: IT
tags: Gnome Desktop Setup Configuration Accessibility 
---

Problem: when having multiple (dark-themed) terminals side by side I find the content hard to read

Solution: increase padding (by a fixed amount of pixels)

~~~terminal
$ cat ~/.config/gtk-3.0/gtk.css:
VteTerminal,
TerminalScreen,
vte-terminal {
    padding: 10px 10px 10px 10px;
    -VteTerminal-inner-border: 10px 10px 10px 10px;
}
~~~

Source: [askubuntu.com](https://askubuntu.com/questions/115762/increase-padding-in-gnome-terminal "increase padding in gnome-terminal")
