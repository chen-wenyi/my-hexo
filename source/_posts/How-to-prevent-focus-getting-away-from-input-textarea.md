---
title: How to prevent focus getting away from input/textarea?
date: 2019-07-09 21:17:18
categories:
- Javascript
tags: 
- event
- preventDefault
---

**Case**
Say we had a `input` element and `button` element. We expect `input` not to lose its focus after clicking `button`.

 ```
 ...
 handleMouseDown(event) {
  event.preventDefault()
 }

 render() {
   return (
     <input />
     <button onMouseDown={event => this.handleMouseDown(event)}></button>
   )
 ...
 }
 ```

 We can invoke `preventDefault` when `mousedown`. Then focus will not get away from `input`.