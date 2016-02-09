#Functions in JavaScript

A JavaScript function is a block of code designed to perform a particular task.

A JavaScript function is executed when "something" invokes it (calls it).

Example
```
function myFunction(p1, p2) {
  return p1 * p2;       // The function returns the product of p1 and p2
}
```

Functions are the core medium for activity in a program written in a functional programming style. The alternative way of defining relationships between and operations on data is Object-Oriented programming.

The central activity in OOP is composing new objects which own data and extending existing objects by adding new methods to them. Data is manipulated through changes of state and mutability. More on OOP in another file soon.

The central tenet of FP is a loose coupling to data, preferring manipulating data through small methods which can combine to perform larger tasks in what's known as "composition".

FP tends to use fewer lines of code than OOP because FP doesn't require building classes for creating objects. FP is a model whereby computations are exclusively expressed as the combination of (mathematical) functions. Since FP doesn't deal with changes of state, information about the data doesn't need to be stored and traced, what's important is the parameters and the return values.

To choose between which paradigm is best to use, Michael Fogus [suggests](/http://blog.fogus.me/2013/07/22/fp-vs-oo-from-the-trenches/):
* Whenever I write some code to deal with data *about* people then **functional programming** seems to work best.
* Whenever I write some code to *simulate* people then **object-oriented programming** seems to work best.

For a robust discussion about the difference between FP and OOP, see [this Quora thread](/https://www.quora.com/What-does-object-oriented-programming-do-better-than-functional-programming-and-why-is-it-the-most-popular-paradigm-when-everybody-seems-to-say-functional-programming-is-superior).

##Use of functions

Functional programming has two fundamental design patterns; nouns and verbs. For nouns, there is immutable data, for verbs, there is referentially transparent functions (returning the same output per input).

The nouns in JavaScript are represented by objects or data, verbs by functions. Functions themselves can be reused to take actions with different sets of data or objects at various points in a program. Functions can even use themselves as a parameter in a process called recursion. This reusability of functions is one of the key benefits of functional programming.

##Function Declaration

There are two ways of defining functions in JavaScript. One is valid for all functions in JS, the other is for ES6 (and, presumably, onwards).

The traditional function declaration is syntactically written like so:
```
function name([param[, param[, ... param]]]) {
   *statements*
}
```

Example:
```
function makeNoise() {
  console.log("Pling!");
};

makeNoise();
// → Pling!

function power(base, exponent) {
  var result = 1;
  for (var count = 0; count < exponent; count++)
    result *= base;
  return result;
};

console.log(power(2, 10));
// → 1024
```

The new ES6 function, called an *arrow function* or *fat arrow function*, has a shorter syntax and lexically binds the `this` value referring to the enclosing execution context's `this`. It requires 'strict' when being used. Syntax:
```
(param1, param2, …, paramN) => { statements }
```

The `this` in JavaScript is like the natural language pronoun "he" which refers to the antecedent noun in the way that the `this` refers to the object that the function is bound to.

Inside an ordinary function, the value of `this` depends on how the function is called - using `strict` or not. When not in `strict` mode, the value of the `this` must be set to an object, so the default is the enclosing execution context, such as the global object or otherwise. In `strict` mode, the value of `this` remains at whatever it is set to when entering execution mode.

##Function keywords

Keywords are special words in JS reserved for particular uses.

"**Function**" - used in ES5 JS to invoke a function.
 "**new**" - used when calling a constructor function to create a new object

"**var**" - declares a variable in the current execution context (i.e. current function or global) and can be reassigned as necessary.
"**let**" - used to define variables limiting their scope to the block in which they are declared.
""**const**" -  follow the same scope rules as variables but can't be re-declared, in other words they're constant.

##Function Invocation

There are four ways to invoke a function in JavaScript.

###As a function
When a function is called without a parent object, the global `this` is invoked.  
For example, this will return the window object:
```function myFunction() {
    return this;
}
myFunction();
```

###As a method
In JavaScript functions can be written as object methods, to manipulate state and interact with other objects.

For example, the following object has a method "fullName" which when called will return "John Doe".

```var myObject = {
    firstName:"John",
    lastName: "Doe",
    fullName: function () {
        return this.firstName + " " + this.lastName;
    }
}
myObject.fullName();
```

###With a function constructor
If a function invocation is preceded with a *new* keyword, it is a constructor function. This creates a new object, inheriting the properties and methods from its constructor.

For example, the following code will return "John":

```
// This is a function constructor:
function myFunction(arg1, arg2) {
    this.firstName = arg1;
    this.lastName  = arg2;
}

// This creates a new object
var x = new myFunction("John","Doe");
x.firstName;
```

###With a function method
*call()* and *apply()* are both predefined JavaScript function methods. Both methods can be used to invoke a function, and both must have the owner object as their first parameter.

This will return 20:
```
function myFunction(a, b) {
    return a * b;
}
myObject = myFunction.call(myObject, 10, 2);
```

##First-class functions

In JavaScript FP, functions are treated as 'First-class functions'. This means that it's possible to pass functions as arguments to other functions, returning them as the values from other functions and assigning them to variables or storing them in data structures.

Second-class functions exist within an imperative functional programming paradigm.

##Higher-order functions

These types of functions take one or more functions as arguments and/or returns a function upon execution. All other functions are first-order (not to be confused with first-class, which is a higer-order function type).

`Map` is an example of a higher-order functions, which takes a function and an array as parameters and returns a new array.

Higher-order functions can be used to:
* Create new functions
* Change other functions
* Provide new types of control flow

This is a higher-order function:
```
function greaterThan(n) {
  return function(m) { return m > n; };
}
var greaterThan10 = greaterThan(10);
console.log(greaterThan10(11));
// → true
```

###Abstraction

Higher-order functions are useful for abstracting functional elements of code into smaller pieces to then compile for execution. For example, you could use the following code to console log each element of an array in an ordinary function:
```
var array = [1, 2, 3];
for (var i = 0; i < array.length; i++) {
  var current = array[i];
  console.log(current);
}
```

Abstracting this into a function, you get:
```
function logEach(array) {
  for (var i = 0; i < array.length; i++)
    console.log(array[i]);
}
```

This is cleaner and simpler, and reduces propensity for bugs. Taking this one more step, we can remove the 'verb' aspect of this function so we can do whatever we want with the array, like so:
```
function forEach(array, action) {
  for (var i = 0; i < array.length; i++)
    action(array[i]);
}

forEach(["Wampeter", "Foma", "Granfalloon"], console.log);
// → Wampeter
// → Foma
// → Granfalloon
```

The above code is an abstraction but not a higher order function because the function is not taking or returning another function.

##Anonymous functions
An anonymous function is a function that was declared without any named identifier to refer to it. As such, an anonymous function is usually not accessible after its initial creation.

The most common use of anonymous functions is as arguments to other functions.

Example of an anonymous function:
```
var x = function (a, b) {return a * b};
var z = x(4, 3);
```

##Callbacks

A callback function is a function that is passed as an argument to another function and is invoked after some kind of event.

This is a piece of executable code passed as an argument to other code which is expected to call back (execute) the argument as some defined time. The invocation may be immediate as in a **synchronous callback** or it might happen at a later time as in an **asynchronous callback**.
