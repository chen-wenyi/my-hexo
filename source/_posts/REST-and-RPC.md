---
title: REST and RPC
date: 2019-09-10 21:12:53
categories:
- REST & RPC
tags:
- REST
- RPC
---

{% note default %}
Both REST and RPC are not framework, they're architecture styles.
{% endnote %}


**REST** - Representational State Transfer
It is Resource Oriented.
Use `Post Get Put Delete` as **Actions** and `url` represents **resource** (i.e.  GET /rest/api/dogs)
REST is based on HTTP Application Layer (w/o Socket)

**RPC** - Remote Procedure Call
It is Action Oriented.
RPC is based on TCP Transport Layer (with Socket)

**REST** is more Lightwight than **RPC**
**RPC**'s Performance is better than **REST** 

## RPC or REST for distributed System?
Internal(Between Modules/Services)
We use RPC since we can call remote methods just like do it locally and get better performance.
External -> REST

![](/images/RPC_Arch.png)
