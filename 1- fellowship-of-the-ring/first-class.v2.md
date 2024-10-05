# Composable Software Construction

## This class is based off of 2 ideas: 
1. That you have worked with a typed language before
2. That you are familiar with fat arrow notation

QUICK REFRESHERS ON THOSE CONCEPTS?
(Code references from Lakin)[https://gist.github.com/lakinwecker/ff524645f25981cd9692b1bef60c7e67]

## Takeaways from this class
Why does this help us write better code? Why do we like this?

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
---------
## Lesson 3: Higher Order Functions
### Pure vs impure functions
- Impure functions have side effects: 
    - Anything that changes about a program that can't be observed by the output  of a function
    - EX: printing to the console, updating a DB

### What is a higher order function? 
A: In mathematics and computer science, a higher-order function (HOF) is a function that does at least one of the following:

- takes one or more functions as arguments (i.e. a procedural parameter, which is a parameter of a procedure that is itself a procedure),
- returns a function as its result.
---------

## Lesson 4: Partial Application 
### Definitions: 
- Application: The process of applying a function to its arguments in order to produce a return value.

- Partial Application: The process of applying a function to some of its arguments. The partially applied function gets returned for later use. In other words, a function that takes a function with multiple parameters and returns a function with fewer parameters. Partial application fixes (partially applies the function to) one or more arguments inside the returned function, and the returned function takes the remaining parameters as arguments in order to complete the function application.

- Curry: A function that takes a function with multiple parameters as input and returns a function with exactly one parameter.

(Cool video on the topic)[https://www.youtube.com/watch?v=XcS-LdEBUkE]

(A good breakdown of concepts)[https://medium.com/javascript-scene/curry-or-partial-application-8150044c78b8]

---------
## Lesson 5: Practical application

** TODO: convert these to TS, I ran out of time :) 
```ts 
 function addThree(num: int): int => {
    return num+3
 }
 ```

 ### Array.map()
- The `Array.map()` method creates a new array from an existing one.
- It loops through each item in the original array, transforms it in some way, and then pushes it into a new array. All of this happens behind-the-scenes.
- For example, let’s say you had an array of numbers, and you wanted to create a new array with the numbers doubled: 

```js
let numbers = [3, 11, 42];
let doubled = [];

numbers.forEach(function (number) {
    doubled.push(number * 2);
})
```

- With `Array.map()`, you don’t have to create the doubled array beforehand. You can define the variable as the output of `Array.map()`.
 - Inside the `Array.map()` callback function, return the value you want added to the array. Under-the-hood, `Array.map()` loops through each item in the original array, runs your callback method on each item, creates a new array, and pushes whatever you return to it: 

```js
let doubled = numbers.map(function (number) {
	return number * 2;
});
```

(live demo link)[https://codepen.io/Kat-Connolly/pen/gOyJyWN?editors=1111]

// Time for .filter?