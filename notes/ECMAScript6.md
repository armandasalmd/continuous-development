## ES6 compared to ES5

[Blog link](https://engineering.carsguide.com.au/es5-vs-es6-syntax-6c8350fa6998)

> EcmaScript (ES) is a standardised scripting language for JavaScript (JS). The current ES version supported in modern browsers is ES5.

#### Arrow function (=>)

```js
// ---------- ES5 ----------
function getNum() {
	return 10;
}
// ---------- ES6 ----------
const getNum = () => 10;
```

or

```js
// ---------- ES5 ----------
function calcCircleArea(radius) {
	return Math.PI * radius * radius;
}
// ---------- ES6 ----------
const calcCircleArea = radius => Math.PI * radius * radius;
```

#### Object Manipulation

1. Extract object values

```js
var obj1 = { a: 1, b: 2 };
// ---------- ES5 ----------
var a = obj1.a;
var b = obj1.b;
// ---------- ES6 ----------
var { a, b } = obj1;
```

2. Property shorthand

```js
var a = 1;
var b = 2;
// ---------- ES5 ----------
var obj1 = { a: a, b: b };
// ---------- ES6 ----------
var obj1 = { a, b };
```

3. Merge objects with the spread operator (…)

```js
var obj1 = { a: 1, b: 2 };
var obj2 = { c: 3, d: 4 };
// ---------- ES5 ----------
var obj3 = Object.assign(obj1, obj2);
// ---------- ES6 ----------
var obj3 = { ...obj1, ...obj2 };
```

4. Async Function (Callback vs. Promise)

```js
// ---------- ES5 (callback) ----------
function isEvenNumber(num, callback) {
	if (num % 2 === 0) {
		callback(true);
	} else {
		callback(false);
	}
}
isEvenNumber(10, function(result) {
	if (result) {
		console.log('even number');
	} else {
		console.log('odd number');
	}
});
// ---------- ES6 (promise) ----------
const isEvenNumber = num => {
	return new Promise((resolve, reject) => {
		if (num % 2 === 0) {
			resolve(true);
		} else {
			reject(false);
		}
	});
};
isEvenNumber(10)
	.then(result => {
		console.log('even number');
	})
	.catch(error => {
		console.log('odd number');
	});
```

Promise also has some super useful methods like:

-   Promise.race → returns the first promise in the iterable to resolve
-   Promise.all → returns a promise when all the promises in the iterable have completed

#### Module Exports and Imports

1. Export module

```js
var testModule = { a: 1, b: 2 };
// ---------- ES5 ----------
module.exports = testModule;
// ---------- ES6 ----------
export default testModule;
// ---------- ES6 (child modules) ----------
export const a = 1;
export const b = 2;
```

2. Import module

```js
// ---------- ES5 ----------
var testModule = require(./testModule);
// ---------- ES6 ----------
import testModule from './testModule';
// ---------- ES6 (child modules) ----------
import { a, b } from './testModule';
```

#### Block Scoping (let)

```js
// ---------- ES6 ----------
var num = 0; // num is globally scoped
for (let i = 0; i < 5; i++) {
	// i is block scoped
	num += i;
}
console.log(num); // 0 + 1 + 2 + 3 + 4 = 10
console.log(i); // undefined
```

#### Template Literal (`)

```js
const a = 1;
const b = 'b';
// ---------- ES5 ----------
const c = 'value of a is ' + a + ' and value of b is ' + b;
// ---------- ES6 ----------
const c = `value of a is ${a} and value of b is ${b}`;
```
