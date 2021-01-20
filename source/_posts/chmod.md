---
title: chmod
tags:
  - chmod
categories: [Linux, shell]
date: 2021-01-20 16:25:07
---

`chmod - change file modes or Access Control Lists`

There are three classes:

- Owner
- Group
- Other Users
<!-- more -->

![](/images/chmod_0.jpeg)

`chmod [ugoa...][[+-=][rwxX]...][path]`
u: Owner g: Group o: Others a: All
+: Add -: Del =: Only (i.e. chmod u=r file only read access)
r: Read w: Write x: Execute

## Octonary Syntax

![](/images/chmod_1.jpeg)
