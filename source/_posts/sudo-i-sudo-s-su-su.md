---
title: 'sudo -i , sudo -s, su, su -'
categories: [Linux, shell]
date: 2021-01-20 15:34:14
---

### sudo -i , sudo -s:

sudo -i will reload environment variables and switch to home dir

sudo -s won't reload and won't switch to home dir

sudo cmd requires current user in `/etc/sudoers`

 <!-- more -->

### su , su -

If current user is not sudoer, su cmd will get root login, but password is mandatory.

su - or su -l equal to sudo -i

su equal to sudo -s
