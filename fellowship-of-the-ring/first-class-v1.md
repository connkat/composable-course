# Class 1

## Understanding Functions

(Lakin's Diagram)[assets/class-1-functions.png]

name: param -> return
ex: 
1. `addThree: Int + Int`
2. `addThree x = x + 3`
    - where `x` is the input param and `x+3` is the return value
3. `addThree(1) = 4`
    - where `1` is the argument

/* do we talk about mapping/relationship diagram here?  ([pg 2](https://drive.google.com/drive/u/0/folders/1UmkQXJQmAskiqhdkjV3sUzObX9ud2Lu9))

IE sets => types
*/

## Pure vs impure functions
- Impure functions have side effects: 
    - Anything that changes about a program that can't be observed by the output  of a function
    - EX: printing to the console, updating a DB

## What is a higher order function? 
A: In mathematics and computer science, a higher-order function (HOF) is a function that does at least one of the following:

- takes one or more functions as arguments (i.e. a procedural parameter, which is a parameter of a procedure that is itself a procedure),
- returns a function as its result.

## What are types?
- Data types, which you are already familiar with like `string`, `boolean`, `int`, etc. 
- We can also use them to create 'type safety', IE let developers know ahead of compiling their code if what they are sending to their function can actually be used the way it is intended. 

### Translate from JS to TS: 
(run in TS playground)
 ```js
function addThree(num) => {
    return num +3
}
 ```

 ```ts 
 function addThree(num: int): int => {
    return num+3
 }
 ```
 - if we attempt to pass a string as an argument, typescript will stop us ahead of time and let us know that we need to send an int because we want to perform some math on the argument passed in and we can't do that with a boolean or string or another data type. 
 - Similarly, if we are calling this function and expecting an int but receive something else as the output, we can find out ahead of time. 

 ### Translate your own function
 - Write a simple JS function (similar to addThree) and now translate it to TS. 

 ## Understanding methods

 - We take methods for granted. They do a lot of work under the hood. 
 - You may have heard the term syntactic sugar before. It’s a term that describes syntax (ways of writing code) that provide shortcuts, and make the code easier to write or read. Array methods like map(), filter(), find(), and reduce() are considered syntactic sugar.

Ironically, they often make things harder to read for beginners, because they hide what’s really happening behind the scenes.

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

### Array.filter()
- Now it it your turn to try, we're going to work with `Array.filter()`.
- Imagine that you have an array of data. Perhaps it’s a list of creatures from Middle Earth and their alliance and you want to find out which ones are good or bad: 
 
 ```js
 let beings = [
	{
		name: 'Hobbit',
		alliance: 'good'
	},
	{
		name: 'Orc',
		alliance: 'evil'
	},
	{
		name: 'Elf',
		alliance: 'good'
	},
    	{
		name: 'Uruk hai',
		alliance: 'evil'
	},
	{
		name: 'Wizard',
		alliance: undefined
	}
];
 ```

 ------------------------------------------- STOP AND LET THEM TRY -------------------------------------------
### Possible Answers: 

- With `Array.forEach()`, you would create a new array. Then you would loop through the beings array and push matching beings to your new array.

```js

function findBaddies(beings) {
    let baddies = [];

    beings.forEach(function (being) {
        if (being.alliance === 'evil') {
            baddies.push(being);
        }
    });
}
```

- With `Array.filter()`, you don’t have to create the new array beforehand. You can define the variable as the output of `Array.filter()`.

Inside the `Array.filter()` callback function, return true if the item should be added to the new array, and false if it shouldn’t. Under-the-hood, `Array.filter()` loops through each item in the original array, runs your callback method on each item, creates a new array, and pushes the items that return true.

```js
function filterBaddies(beings){
    let baddies = beings.filter(function (being) {
        return being.alliance === 'evil'
    });
}
```
(live demo link)[https://codepen.io/Kat-Connolly/pen/abxrxVY?editors=1011]

### Make it more reusable
- This code is good, but it only works in this single scenario. If I try to pass it an array of objects with different key/value pairs and filter for a different value, this won't work.

```js
function filterGeneric(argArray, argKey, argValue){
    let output = argArray.filter(function (arg) {
        return arg.argKey === 'argValue'
    });
}
```


---------------------
## Notes: 
### Missing: 
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
- Why does this help up write better code? Why do we like this?