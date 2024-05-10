# Composable Software Construction

## This class is based off of 2 ideas: 
1. That you have worked with a typed language before
2. That you are familiar with fat arrow notation

QUICK REFRESHERS ON THOSE CONCEPTS?
(Code references from Lakin)[https://gist.github.com/lakinwecker/ff524645f25981cd9692b1bef60c7e67]

## Takeaways from this class
Why does this help up write better code? Why do we like this?

## Lesson 1: functions and types

What is the output of this function: 
```js
 const formatAbsOfNegative1 = () =>
    console.log(`The absolute value of -1 is ${Math.abs(-1)}`);
```
- This function is completely static. You can even say that it is constant.
- You will always get the same output and there are no parameters, we change this by passing it an argument: 
```js
 const formatAbsOfNegative1 = (num) =>
    console.log(`The absolute value of num is ${Math.abs(num)}`);
 ```

- Add now for Typescript: 
```ts
 const formatAbsOfNegative1 = (num: any): string =>
    console.log(`The absolute value of num is ${Math.abs(num)}`);
```

- But what happens when we pass a value that isn't numerical? 
```ts
const num = "Joe";
 const formatAbsOfNegative1 = (num: any): string =>
    console.log(`The absolute value of num is ${Math.abs(num)}`);
```

- This is where strictly typing a language can be helpful: 
```ts
const num = "Joe";
 const formatAbsOfNegative1 = (num: int): string =>
    console.log(`The absolute value of num is ${Math.abs(num)}`);
```

---------

## Lesson 2: Making it more dynamic 

- The function now takes in a single argument, which makes it slightly less static, but how can we make it even more dynamic? 

```ts
 const formatOperation = (x: any, operation: any): string => 
    console.log()`The ??? of ${x} is ${op(x)}`);
    
    formatOperation(2, Math.abs));
```

- But look, JS doesn't account for this as an issue if we try to perform a mathematical function on a string: 
```js
 const formatOperation = (x, operation) => 
    console.log()`The ??? of ${x} is ${op(x)}`);
    
    formatOperation( 'Dirt', Math.abs));    
```

- What is the bug here: 
```ts
 const formatOperation = (x: int, operation: any): string => 
    console.log()`The ??? of ${x} is ${op(x)}`);
    
    formatOperation(-2, Math.abs));
```

- And just to make it more dynamic, let's throw in a name: 
```ts
 const formatOperation = (name: string, x: int, operation: any): string => 
    console.log()`The ${name} of ${x} is ${op(x)}`);
    
    formatOperation(-2, Math.abs));
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
