---
id: izbt415ae1injc41kihz3dz
title: falsy value
desc: ''
updated: 1697446496098
created: 1697446251960
---

# Javascript difference between null, undefined or undeclared

undefined
* A variable that has been declared but not assigned a value is undefined.
* It's the default value of function parameters that are not provided when the function is called.
* If a function doesn't explicitly return a value, it will return undefined.

undefined is a primitive type , and null is also a primitive type. .To check for it, compare using the strict equality (===) operator or typeof which will give the 'undefined' string. Note that you should not be using the abstract equality operator to check, as it will also return true if the value is null.

`null == undefined` true, `null === undefined` false

A variable that is null will have been explicitly assigned to the null value. It represents no value and is different from undefined in the sense that it has been explicitly assigned

null:
* null is an assignment value. It represents the intentional absence of any object value.
* It needs to be explicitly assigned to a variable.


``` javascript
var foo;
console.log(foo); // undefined
console.log(foo === undefined); // true
console.log(typeof foo === 'undefined'); // true

console.log(foo == null); // true. Wrong, don't use this to check!

function bar() {}
var baz = bar();
console.log(baz); // undefined
```

So, in summary:
* For **primitives**: Assignment is by value. Modifying one variable doesn't affect others with the original value.
* For **non-primitives (objects)**: Assignment is by reference. Modifying the object affects all variables pointing to that object, but reassigning one of those variables to a new object doesn't change the others.


#Frontend   #javascript