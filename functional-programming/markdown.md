class: center middle front hljs-default
# Intro to Functional Programming

---
class: inverse hljs-default

# Agenda

1. What it is
  a. Intro
  b. Core Concepts
2. Why does it matter?
3. Cool Demo

---

# what is a function?

```javascript

function x (number) {
return number + 1;
}

```

A function is something that takes in an **input** and returns an **output**

---

.leftSplit[

##### Imperative

```js
let str = "Perry is awesome.";
str = "Eddie is also awesome!";
console.log(str);

// Perry is awesome. => Eddie is also awesome!

```
]

.rightSplit[

##### Functional (declarative)

```js

function fix(str) {
  return newStr = "Eddie is also awesome!"
}

let str = "Perry is awesome."
let newStr = fix(str);
console.log(newStr);

// Perry is awesome => Eddie is also awesome!
```
]

---
```js
 ask([TECH_STACK])()
      .then(mergeConfig)
      .then(ask([REPO_NAME]))
      .then(mergeConfig)
      .then(ask([USE_HTTPS]))
      .then(ask([USE_REPO]))
      .then(mergeConfig)
      .then(askRepoDetails)
      .then(resolve)
      .then(null, reject);
```
---
class: inverse hljs-default center
# Core Concepts
---

# Pure Functions

.leftSplit[
Non-Pure Function
```javascript

let x = 1;

function add() {
  return x = x + 1;
}

let final = add();
let finalAgain = add();

```
]

.rightSplit[
Pure Function
```javascript

function add(x) {
  return x = x + 1;
}

let final = add(1);
let finalAgain = add(1);

```
]
---

# Pure functions

- given the same input, returns the same result everytime
- have no **side-effects**
- side-effects are the root of all evil

---

# Higher Order Functions

- functions that take in other functions as input and/or return functions as output

```javascript
// lets make add x = x + 2

function addOne(x) {
  return x = x + 1;
}

function modifyAdd(func) {
  let newFunc = function(x) {
    func(x) + 1;
  }
  return newFunc;
}

let addTwo = modifyAdd(addOne);

```

---

# Immutability

Mutable

```javascript
let obj = { greeting = "hi" };
obj.greeting = "hello";
// obj = { greeting = "hello" };
```

Immutable

```javascript
let obj = { greeting = "hi" };
let newObj = _clone(obj);
newObj.greeting = "hello";
// obj = { greeting = "hi" };
// newObj = { greeting = "hello" };
```

---
class: inverse hljs-default center
# Why does it matter?

---

# Simpler to maintain

*video*

---

# Why is there less code?

- utility functions

```js
function modifyArray(array){
  let newArray = /* modify array */
  return newArray;
}
```

- lodash, ramda, underscore 

---

# Simple vs Easy

```js
let sumOfEvenSquares = _.chain(numbers)
    .filter(n => n % 2 === 0)
    .map(n => n * n)
    .sum()
    .value();
```

---

# Simple vs Easy

image

---

# Pure functions are much easier to test

```js
function getY() {
  return y = x +1;
}

x = 1;
x = 50;

assert.equal(getY(), getY());
```

---
class: inverse hljs-default center

# State

---

# State

- state = variables?

```js
x = 1;
x = 50;

function getY() {
  return y = x +1;
}
```

what does y return?

---
class: center

# Time

---

# Variables

- represent a single point in time

- single-thread + single timeline
- issues with concurrency

- things don't change in place, time as a dimension
- the future is a function of the past and doesn't change it

---

# Immutability  

not something that just knwoing how to write pure functions can solve
```js
function getY() {
  return y = x +1;
}

x = 1;
x = 50;

assert.equal(getY(), getY());
```
---

immutability
diffs

---

immutability
persistent data structures (linked lists) diffs

---

# Why now?
memory

---

# Why now?
cores
---
