#Javascript

Javascript is a computer language established in 1995 by founder Brendan Eich from Mozilla. It enables browsers to render HTML interactively by using AJAX (asynchronous javascript and XML), without the need to refresh the browser. It's standardised as ECMAscript, with its newest release in 2015, ES6. All browsers support Javascript and it's considered the language of the web.

When the browser client sends a GET request to a server, Javascript code is read line-by-line as it is an interpreted language not requiring a compiler.

Javascript can be written in an Object-Oriented style or functionally. In object oriented programming (OOP), everything is considered an object with state and behaviours. Classes are used to define the objects, and states and behaviours are translated in members and methods. In functional programming, functions are used to perform individual tasks. Functions can be used over and over again, can be passed as arguments and can call themselves (recursion). Functions are useful tools to enable modular-style development.

Apps can be designed either functionally, object-oriented or both.

##Getting started

###Node and the Console

While Javascript is supported on browsers (client), not all apps run exclusively on the client-side - sometimes a 'back-end' is required to add extra functionality such as database interfacing, handling HTTP requests and serving content. To run in the server, JS requires a compiler in the console, and for that we use Node.js. According to their [website](https://nodejs.org/), Node is a Javascript runtime environment built on Chrome's V8 Javascript engine. So, Node is used to handle HTTP requests and run Javascript code on the server (the computer running the app). With Node, you can implement packages in your code which provide features not native to Javascript.

First, install Node from the website. Then, to run node in your computer, do:
```
$ node
```

Now, you can run Node commands in the console, such as:
```
>console.log("Hello World");
Hello World
undefined
>
```

Or, run a Javascript file with:
index.js
```
console.log('Hello World')
```
Console
```
$node index.js
Hello World
```

###File I/O

Node.js makes using libraries and external files easy with its fs commands such as fs.readFile. Readfile takes a path and a callback (which is executed once the file is read)

Example from [An Absolute Beginners Guide to Node.js](/http://blog.modulus.io/absolute-beginners-guide-to-nodejs)
```
// Load the fs (filesystem) module.
var fs = require('fs');

// Read the contents of the file into memory.
fs.readFile('example_log.txt', function (err, logData) {

// If an error occurred, throwing it will display the exception and kill our app.
  if (err) throw err;

// logData is a Buffer, convert to string.
  var text = logData.toString();

var results = {};

// Break up the file into lines.
  var lines = text.split('\n');

lines.forEach(function(line) {
    var parts = line.split(' ');
    var letter = parts[1];
    var count = parseInt(parts[2]);

if(!results[letter]) {
      results[letter] = 0;
    }

results[letter] += parseInt(count);
  });

console.log(results);
  // { A: 2, B: 14, C: 6 }
});
```

##Writing JavaScript

Outside the scope of this tutorial, but useful to understand for full context of what JavaScript code does, is the ECMAScript lexical grammar, which is how text is interpreted and read by the program and is described [here](/https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar) on MDN's developer website. 

###Strings

In javascript a bunch of letters, numbers and words enclosed in single or double quotation marks is known as a string.

Examples
```
"Charlie bit my finger."
'2, 4, 6, 8 I woke up too late.'
```

###Variables

Values are the simplest components in Javascript. Values include: `1`, `true`, `"hello"` `function(){}`. Variables store Values.

A JavaScript identifier must start with a letter (case sensitive), underscore or dollar sign. Subsequent characters can include numbers(0-9). Variables have a scope (an environment within which they are defined). This can be local or global - in reality all variables are local; some just more than others. It is possible to declare a variable using `var` or `let` without an initial value, causing the variable to be undefined.

Example
```
var a;
console.log("The value of a is " + a); // logs "The value of a is undefined"
console.log("The value of b is " + b); // throws ReferenceError exception
```

###Functions

There are functions that modify or create values and return them and
functions take in values and perform some action that cannot be returned.
JavaScript's dynamic capabilities include runtime object construction, variable parameter lists, function variables, dynamic script creation (via eval), object introspection (via for ... in), and source code recovery (JavaScript programs can decompile function bodies back into their source text).

Functions require an input (parameter), and `return` a value when invoked. Different functions expect different inputs depending on how they were constructed.

The function declaration looks like this:
```
function name([param[, param[, ... param]]]) {
   *statements*
}
```

A fat arrow function (used in ES6 and requires 'strict') is declared like so:
```
(param1, param2, …, paramN) => { statements }
```

####Making new functions

Example
```
var square = function(number) { return number * number };
var x = square(4) // x gets the value 16
```

See more on functions in JavaScript [here](/functions.md).
