---
title: 'Where''s ''this'' pointing to?'
date: 2019-07-06 15:15:37
categories: 
- Javascript
tags:
- es6
- this
- arrow function
---


{% note default %}
It's vague to locate where does `this` point to inside function between arrow function and regular function sometimes. That's true.
{% endnote %}

# Definition
[Arrow Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) is the new feature of [**ECMAScript 6**](http://es6.ruanyifeng.com/). 

`() => {}`

# Problem

where does `this` refer to inside a arrow function from code below?
 <!-- more -->
```
function foo() {
    return () => {
      console.log(this.a)
    }
}

const obj1 = {a:1}
const obj2 = {a:2}

const bar = foo.call(obj1)
bar.call(obj2)
```

Which `a` would be print out between obj1 and obj2 ?

What if we modify the arrow function into regular one? What's the result then.

```
function foo() {
    return function(){
      console.log(this.a)
    }
}

const obj1 = {a:1}
const obj2 = {a:2}

const bar = foo.call(obj1)
bar.call(obj2)
```

# Answer

Inside a **arrow function**, foo is bind to obj1 firstly. Therefor, `this` points to obj1. However **arrow function** never changes where this refer to. And `this` keep consistent with outer function's no matter how obj2 binding to arrow function later. Since `this` is bind to arrow function at the definition (lexical scope) not run-time. 

**tips：**
lexical scope also named static scope. Scope would be determined during definition. So `this` would be resolved from inside to outside for arrow function.

```
var x=1;
var obj={
  x:2,
  /**
  looking for this. there is no this in obj, so looking outside until global(windows), so this.x =  windows.x 
  */
  print: () => { 
    console.log(this.x)
  }
}
obj.print();
```

```
var x=1;
var obj={
  x:2,
  print: function() { // regular function according to 'context'
          console.log(this.x)
         }
}
obj.print();
```

```
var a = 1
var obj = {
  a:2,
  b:{
    a:3,
    c: {
      a:4,
      getA: ()=> { // global (windows)
        console.log(this.a)
      }
   }
  }
}

obj.b.c.getA()
```

```
var a = 1
var obj = {
  a:2,
  b:{
    a:3,
    c: {
      a:4,
      getA: function() { // context -> this = c
                         // looking for this -> c
              return () => console.log(this.a)
            }
   }
  }
}

obj.b.c.getA()()
```

#Conclusion

For arrow function, we look for `this` according to **lexical scope**. For regular function, we do in terms of `context`.

In short, who invoke regular function, `this` point to who. (run-time)

For arrow function, looking for `this` from inside to outside, first `this` is its `this` scope. (during definition)
