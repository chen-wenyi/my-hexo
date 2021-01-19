---
title: Go Format Placeholder
date: 2020-01-25 17:29:17
categories:
- Go
tags:
- Printf
---

`%v` output struct    {10 30}
`%+v` output struct with fields   {x:10 y:30}
`%#v` output struct with fields and type name   main.Point{x:10, y:30}
`%T` output type    main.Point
`%t` output bool    true
`%d` output decimal   100
`%b` output binary    99 -> 1100011
`%c` output char    99 -> c
`%x` output hexadecimal   99 -> 63
`%f` output float number    99.9 -> 99.900000
`%e` output via scrientific notation    123400000.0 -> 1.234000e+08
`%E` output via scrientific notation    123400000.0 -> 1.234000e+08
`%s` output string    string
`%q` output string with quotation mark    "string"
`%p` output the pointer   &abc -> 0xc00004a090
`%2.2f` output float with width and precision   1.2 ->  1.20




