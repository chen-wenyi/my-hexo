---
title: IF ELSE in Shell Script
categories: [Linux, shell]
date: 2021-01-19 20:49:04
---

# If else in shell script

## Basic Syntax

```
if [  ]; then

else

fi
```

 <!-- more -->

## Number Comparison

```
[ $a -eq $b ]    equal
[ $a -ne $b ]    not equal
[ $a -gt $b ]    great than
[ $a -lt $b ]    less than
[ $a -ge $b ]    great than or equal
[ $a -le $b ]    less than or equal
```

## String Comparison

```
str="abc"
If [[  ! $str ]]; then
    echo True
else
    echo False

# False
```

```
str="abc"
If [[ $str ]]; then
    echo True
else
    echo False

# True
```

```
str="abc"
If [[ $str == abc ]]; then
    echo True
else
    echo False

# True
```

```
str="abc"
If [[ $str != abc ]]; then
    echo True
else
    echo False

# False
```

## File Comparison Operators

```
-e filename  if filename exists，return true
-d filename  if filename is directory，true
-f filename  if filename is normal file，true
-L filename  if filename is symbolic link, return true
-r filename  if filename is readable, return true
-w filename  if filename is writable, return true
-x filename  if filename is excutable, return true

Usage:

if [ ! -d test ];then
  mkdir test
else
  echo dir exist
fi

```
