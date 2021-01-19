---
title: Vultr SS Deployment
date: 2020-02-01 11:21:55
categories:
  - ss
tags:
  - ss
  - vultr
---

SS Deployment on Vultr

 <!-- more -->

```
git clone -b master https://github.com/flyzy2005/ss-fly

// init ss service
ss-fly/ss-fly.sh -i [password] [port]

// enable bbr
ss-fly/ss-fly.sh -bbr

// alter config
vim /etc/shadowsocks.json

// stop ss service
ssserver -c /etc/shadowsocks.json -d stop

// start ss service
ssserver -c /etc/shadowsocks.json -d start

// restart ss service
ssserver -c /etc/shadowsocks.json -d restart

// uninstall ss
ss-fly/ss-fly.sh -uninstall

```
