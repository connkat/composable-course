# Composable Software Construction

## This class is based off of 2 ideas: 
1. That you have worked with a typed language before
2. That you are familiar with fat arrow notation

QUICK REFRESHERS ON THOSE CONCEPTS

## Takeaways from this class
Why does this help up write better code? Why do we like this?

## Let's talk about functions!

What is the output of this function: 
```js
 const formatAbsOfNegative1 = () =>
    `The absolute value of -1 is ${Math.abs(-1)}`;
```
- This function is completely static. You can even say that it is constant.
- You will always get the same output and there are no parameters, we change this by passing it an argument: 
```js
 const formatAbsOfNegative1 = (num) =>
    `The absolute value of num is ${Math.abs(num)}`;
    ```

- Add now for Typescript: 
```ts
 const formatAbsOfNegative1 = (num: any) =>
    `The absolute value of num is ${Math.abs(num)}`;
```
- But what happens when we pass a value that isn't numerical? 
```ts

const num = "Joe";
 const formatAbsOfNegative1 = (num: any) =>
    `The absolute value of num is ${Math.abs(num)}`;
```

### Question 1: How can we make this more dynamic?
```ts
 const formatOp = (op: any, x: any) => `The ??? of ${x} is ${op(x)}`;
  tryToRun(() => formatOp(Math.abs, -4));
```

- Single param > multi param > partial application
** Partial Application
- Taking a funct and refactoring it together
    - What is static and what is dynamic? 
    - Making a function more dynamic all the way through
        - IE: passing in other functions, types aren't necessary (sub in generic)
    ** this assumes that people are using Typed language
- requires fat arrow notation, single param function 
## V2: 
- Focus on higher order functions with the idea of trying to end up with partial application
- Could be JS or TS?
    Could use this as motivation to introduce TS
- Get through enough theory so that we can walk through things like map, and then leave them with some potential practical examples
