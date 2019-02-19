---
layout: post
title: Subleties vs Time Management
category: IT
tags: Ansible YAML subleties
---

Sometimes it's embarassing how a weak editor setup combined with a bad font can waste half an hour or more.

In the following Ansible task snippet from a role is a subtle error, that's barely visible with a poor font:

~~~terminal
- name: Setup UFW for OpenSSH
  ufw:
    ruĺe: limit
    name: OpenSSH
  tags:
    - security
    - configuration
~~~

And no matter how much verbosity is increased the important information is already contained within the main error message.
But that doesn't help -- with a cheap font.

~~~terminal
"msg": "Unsupported parameters for (ufw) module: ruĺe Supported parameters include: app, comment, ..., rule, ...
~~~

I must have hit an apostroph instead of backspace (german keyboard layout) without noticing.
And indeed syntax highlighting is worthless if it only shows low-level correctness -- in this case, not much won: that it's proper YAML.
Without the Ansible specifics that only enforces a sense of false security.

I definitivly need a better editor setup or IDE for Ansible roles.
One that screems right into my face that I'm using an unknown key(word).

And just in case you didn't notice by now, the problem was: l vs ĺ (lowercase L vs. lowercase L with apostroph) in "rule".
