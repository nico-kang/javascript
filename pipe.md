## we are say pipe function in javascript

Pipe function to our will some small functions are arbitrarily grouped together, so more convenient and clear

For example you now have some simple function
```
const times = (y) =>  (x) => x * y
const plus = (y) => (x) => x + y
const subtract = (y) =>  (x) => x - y
const divide = (y) => (x) => x / y
```
Your pipe() would be used to generate new functions
```
pipe([
  times(2),
  times(3)
])  
// x * 2 * 3

pipe([
  times(2),
  plus(3),
  times(4)
]) 
// (x * 2 + 3) * 4

pipe([
  times(2),
  subtract(3),
  divide(4)
]) 
// (x * 2 - 3) / 4
```
to make things simple, functions passed to pipe() will all accept 1 argument


the steps are as follows

first create an pipe function accept an array include contain multiple composition function

Because pipe will use to generate new function
So Include pipe return an anonymous function and accept one parameter

And then return reduce method and use reduce method to loop multiple simple function in anonymous function, the reduce method will accept two parameter, Number one is single simple function, Number two is original value

And then return simple function and use call method execution to simple function and pass in two parameter, Number one is this, Number two is original value


```
/**
 * @param {Array<(arg: any) => any>} funcs 
 * @return {(arg: any) => any}
 */
const times = (y) =>  (x) => x * y
const plus = (y) => (x) => x + y
const subtract = (y) =>  (x) => x - y
const divide = (y) => (x) => x / y

function pipe(funcs) {
  return function(arg) {
    return funcs.reduce((result,func) => {
      return func.call(this,result)
    },arg)
  }
}

console.log(pipe([
  times(2),
  times(3)
])(2))
// x * 2 * 3

console.log(pipe([
  times(2),
  plus(3),
  times(4)
])(2))
// (x * 2 + 3) * 4

console.log(pipe([
  times(2),
  subtract(3),
  divide(4)
])(2))
```