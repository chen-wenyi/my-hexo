---
title: Is 'dispatch' sync or async function in Redux
date: 2019-07-08 21:28:11
categories:
- Redux
tags: 
- dispatch
- synchronous
- asynchronous
- thunk
- middleware
---


{% note default %}
We apply [**thunk**](https://www.npmjs.com/package/redux-thunk) middleware in `Redux` for performing asynchronous `dispatch`. How is the excution order if dispatching bunch of synchronous/asynchronous functions (action creators)?
{% endnote %}

Below we got two action creators:
 <!-- more -->
```
function increment(number) {
 return {
   type: 'INCREMENT'
   number
 }
}

function incrementAsync() {
 return async (dispatch) => {
    const number = await fetchNumber()
    dispatch(increment(number))
 }
}

function doubleIncrement() {
  return dispatch => {
    dispatch(increment(1)) // A: console.log(dispatch(increment()))
    dispatch(incrementAsync()) // B: console.log(dispatch(incrementAsync()))
  }
}
```
**What would we get at location A and B?**
Answer: An `object`: {type: 'INCREMENT'} and a `promise`.
That means whether `dispatch` is sync or async depends on what content is being dispached.


**Conclusion**
we can maintain the order of `dispatch` with `thunk` middleware like:
```
await dispatch(incrementAsync())
await dispatch(incrementAsync())
```
Or
```
Promise.all([
  await dispatch(incrementAsync())
  await dispatch(incrementAsync())
]).then(...)
```