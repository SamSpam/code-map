#Javascript

Javascript is a computer language established in 1995 by founder Brendan Eich from Mozilla. It enables browsers to render HTML interactively by using AJAX (asynchronous javascript and XML), without the need to refresh the browser. It's standardised as ECMAscript, with its newest release in 2015, ES6. All browsers support Javascript and it's considered the language of the web.

When the browser client sends a GET request to a server, Javascript code is read line-by-line as it is an interpreted language not requiring a compiler.

Javascript can be written in an Object-Oriented style or functionally. In object oriented programming (OOP), everything is considered an object with state and behaviours. Classes are used to define the objects, and states and behaviours are translated in members and methods. In functional programming, functions are used to perform individual tasks. Functions can be used over and over again, can be passed as arguments and can call themselves (recursion). Functions are useful tools to enable modular-style development.

Apps can be designed either functionally, object-oriented or both.

##Getting started - Node and the Console

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

###Variables
Values are the simplest components in Javascript
Values include: `1`, `true`, `"hello"` `function(){}`
Variables store Values

###Functions
* there are functions that modify or create values and return them and
functions take in values and perform some action that cannot be returned
* JavaScript's dynamic capabilities include runtime object construction, variable parameter lists, function variables, dynamic script creation (via eval), object introspection (via for ... in), and source code recovery (JavaScript programs can decompile function bodies back into their source text).
