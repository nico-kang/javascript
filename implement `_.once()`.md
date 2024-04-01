## implement `_.once()`

_.once(func) is used to force a function to be called only once, later calls only returns the result of first call.
Can you implement your own once()?

```
function func(num) {
  return num
}

const onced = once(func)

onced(1) 
// 1, func called with 1

onced(2)
// 1, even 2 is passed, previous result is returned
```

we are target is will onced mutiple call and pass in different parameter but return the first time result

steps are as follows

first we create an onced function and accept an func fucntion

in an function create an result equal null and create switch is isCalled equal false and create an anonymous function only accept one parameter is args and return anonymous function

an anonymous function if isCalled equal true so return result and then use call method called func function and pass in this and args and equal to result

and then the isCalled equal true so next call Stepped up to the judgment and laste return result

```
function once(func) {
  // your code here
  let result = null;
  let isCalled = false;
  return function (...args) {
    if (isCalled) {
      return result
    }
    result = func.call(this, ...args);
    isCalled = true
    return result
  }
}
```