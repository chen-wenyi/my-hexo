---
title: How does async/await work?
date: 2019-08-23 21:29:22
categories:
- Javascript
tags:
- async/await
---

**Facts**
A few things we need to know is that async/await must in pairs.
Actually, when invoking an async function like `asyncFun()`, we got a `Promise` object. If there's a `return` inside **asyncFun**, it will be returned out in the form of `resolve` of `Promise` object like below:

```
async function asyncFunc() {return 1}
console.log(asyncFunc())  // --> Promise {<resolved>: 1}
```
 <!-- more -->
**Experiment**
Now we imitate calling ***Apple*** and ***Banana*** APIs by async/await function. And make a call with and w/o await. See what we got.

 ```
 async function asyncGetApple() {

  console.log('Get Apple Start -->')

  await new Promise(resolve => {
    console.log('Calling Apple Api...')
    resolve()
  }).then(() => console.log('Apple is ready!'))

  await new Promise(resolve => {
    console.log('Calling Apple Api again...')
    resolve()
  }).then(() => console.log('Apple is ready again!'))

  console.log('Get Apple End -->')

}

async function asyncGetBanana() {

  console.log('Get Banana Start -->')

  await new Promise(resolve => {
    console.log('Calling Banana Api...')
    resolve()
  }).then(() => console.log('Banana is ready!'))

  await new Promise(resolve => {
    console.log('Calling Banana Api again...')
    resolve()
  }).then(() => console.log('Banana is ready again!'))

  console.log('Get Banana End -->')

}

function run1() {
  asyncGetApple()
  asyncGetBanana()
}

async function run2() {
  await asyncGetApple()
  await asyncGetBanana()
}

run1()
run2()

 ```

**Result**
Run them yourself. :D
