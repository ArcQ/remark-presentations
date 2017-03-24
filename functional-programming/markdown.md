class: center middle front hljs-default
# Intro to Functional Programming

---
class: inverse hljs-default

# Agenda

1. What it is
2. Why does it matter?
3. Cool Demo

---

.leftSplit[

##### Imperative

```js
let str = "Hi, I'm string 1!";
str = "Hi, I'm string 2!";
console.log(str);

// Hi, I'm string 1!. => Hi, I'm string 2!

```
]

.rightSplit[

##### Functional (declarative)

```js

function fix(str) {
  return newStr = "Hi, I'm string 2!"
}

let str = "Hi, I'm string 1!"
let newStr = fix(str);
console.log(newStr);

// Hi, I'm string 1! => Hi, I'm string 2!
```
]

---
```js
Rx.Observable.fromEvent(worker, 'message')
              .map(function (ev) { return ev.data * 1; })
              .buffer(Rx.Observable.interval(500))
              .where(function (x) { return x.length > 0; })
              .map(function (x) { return x.length; });
```
---

# What is a function?

```javascript

function x (number) {
return number + 1;
}

```

A function is something that takes in an **input** and returns an **output**

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
let obj = { greeting:"hi", to:"everone"};
obj.greeting = "hello";
// obj = { greeting = "hello", to:"everyone" };
```

Immutable

```javascript
let obj = { greeting:"hi", to:"everyone"};
let newObj = _clone(obj);
newObj.greeting = "hello";
// obj = { greeting = "hi", to:"everyone"};
// newObj = { greeting = "hello", to:"everyone"};
```

---
class: inverse hljs-default center
# Why does it matter?

---

# Simpler to maintain

[functional programs have less lines of code](assets/less-lines-of-code.mp4)

---

# Why is there less code?

- utility functions

```js
function modifyArray(array){
  let newArray = /* modify array */
  return newArray;
}
```

- [ramda](http://ramdajs.com/docs/), lodash, underscore 

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

![simple vs easy](assets/simplevseasy.jpg)

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

```js
x = 1;
x = 50;
```

- represent a single point in time
- single-thread + single timeline
- issues with concurrency

"Things don't change in place when you include time as a dimension. The future cannot change the past, but is a function of the past" - Rich Hickey

---

# State as a Function of Time

```js
// current state = { seconds: 0 };
function getNextState() {
  return newState = { seconds: currentState.seconds +1 };
}
let currentState = getNextState();
/*{ seconds: 0 }
{ seconds: 1 }
{ seconds: 2 }
{ seconds: 3 }...*/
```
---

# Immutability and Persistent Data Structures

- makes it much cheaper to create clones of your state
- state is now a function of your time
.rightSplit[![immutability structural sharing](assets/immutable-structural-sharing.png)]

---

# Redux Demo

---

# What is the Future of Functional Programming?
![performance-of-cpu](assets/performance-of-cpu.jpg)

---

# That's it! Questions?
