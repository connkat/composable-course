# Class 1

## Understanding Functions

(I can't draw in an MD, but starting from [p1 of Laiken's notes](https://drive.google.com/drive/u/0/folders/1UmkQXJQmAskiqhdkjV3sUzObX9ud2Lu9))

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
 - Similarly, if we are calling this function and expecting an int bu receive something else as the output, we can find out ahead of time. 

 ### Translate your own function
 - Write a simple JS function and now translate it to TS. 


------------------------------------------------------------------- These are just reference notes that will be removed
## End goal: 
To write existing methods with Generic Syntax:
- .map
- .filter
- etc
--What are these things doing internally for you? 
--How do we express them in a typesafe manner?
--How do we express them generically?

## Themes: 
1. Definitions and overview:
- Defining the parts of a function
- Pure vs impure/side effects
- Referential transparency
** Do a map/filter and see what it does

2. Bigger picture and group application:
- Overview of types, pros/cons
- Isolate and breakdown higher order functions
** Build your own version or map/filter

3. Stepping through and independent application:
- Step through making a common method into a generically typed one
- Break down functions in TS
- Generic types
--Importance of being able to pass in functions as args (high order functs)

** Make existing into generic



------
V1: inclusive of high order, maybe not generics
V2: focus on small and simple functions, apply generically 



