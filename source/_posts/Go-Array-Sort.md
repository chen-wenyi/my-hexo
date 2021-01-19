---
title: Go Slice Sort
date: 2019-09-12 15:54:26
tags:
- Go
- Sort
---

# Customized Slice Sort

We need to implement 3 functions for slice sorting. They are: 
`Len()` length of slice
`Swap()` swap two elem
`Less()` > is DESC and < is ASC

```
package meta

import "time"

const baseFormat = "2006-01-02 15:04:05"

type byUploadTime []FileMeta

func (fMetaSlice byUploadTime) Len() int {
	return len(fMetaSlice)
}

func (fMetaSlice byUploadTime) Swap(i int, j int) {
	fMetaSlice[i], fMetaSlice[j] = fMetaSlice[j], fMetaSlice[i]
}

func (fMetaSlice byUploadTime) Less(i int, j int) bool {
	iTime, _ := time.Parse(baseFormat, fMetaSlice[i].UploadAt)
	jTime, _ := time.Parse(baseFormat, fMetaSlice[j].UploadAt)
	return iTime.UnixNano() > jTime.UnixNano()
}

```

Then we can do the sort
```
sort.Sort(byUploadTime(fileMetaSlice))
```
