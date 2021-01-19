---
title: Change Timezone in Linux
tags:
  - timezone
categories:
  - Linux
date: 2021-01-16 11:24:00
---

# There are three steps

 <!-- more -->

## Step one

`tzselect` to select a timezone

## Step two

generate a varibale from Step one:
`TZ='Asia/Singapore'`

## Step three

copy below and export in _/ect/profile_
`export TZ='Asia/Singapore'`
