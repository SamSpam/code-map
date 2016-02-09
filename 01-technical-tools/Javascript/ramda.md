#Ramda

"A practical functional library for Javascript programmers."

The Ramda set of tools is specifically designed to not mutate data and not produce side-effects. Ramda functions are also automatically curried. Ramda offers roughly the same set of methods as Underscore, but the way it offers them makes functional composition easy.

Initialise with `npm i Ramda`
Import with `import 'R' from ramda`

##Currying

This is a process of turning a function that expects more than one parameter into one which, when supplied fewer parameters, returns a new function awaiting the remaining parameters.

Currying proceeds right-to-left, and when you skip some arguments, Ramda assumes that the latter (right-hand) ones have been left off. So, in R.map, expecting a function and an array, the array is expected to be left off if only one argument is supplied. This leaves you with a map expecting an array with a function baked into it.

##append

Returns a new array with a given element added to it.

```
R.append('beginning', ['In', 'the'])
//["In", "the", "beginning"]
```

##chain

Chain maps a function over a list and concatenates the results.
```
var halve = n => [n, n/2];
R.chain(halve, [1, 2, 3]);
```

##concat

Returns the result of concatenating the given lists or strings.

Dispatches to the concat method of the second argument, if present.
```
R.concat('Hello ', 'World!') // => "Hello World!"
```

##contains

Returns a boolean: `true` if the specified value is equal to at least one element of the given list.
```
R.contains('yo-yo', 'I want to play with a yo-yo') // => true
```

##drop

Returns all but the first n elements of the given list, string, or transducer/transformer (or object with a drop method).
```
var halve = n => [n, n/2];
R.drop(1, R.chain(halve, [1, 2, 3])); //=> [0.5, 2, 1, 3, 1.5]
```

##filter

Takes an array (filterable) and a function (filter) and returns an array (filtered).
```
var isBigEnough = n => n >= 10
R.filter(isBigEnough, [1, 13, 4, 54, 89, 9]) // => [13, 54, 89]
```

##flatten

Takes an array of nested arrays and 'flattens' them into one array.

Here's a bastardised version without the R.flatten function to show what it does.
```
var flatten = R.reduce(R.concat,[]);
flatten([[1,2],[3,4]])//=>[1,2,3,4]
```
Can be simplified / written properly as:
```
R.flatten([[1,2],[3,4]])//=>[1,2,3,4]
```

##forEach

Takes a function and an array and returns the same array, and the result of the function manipulating each item in the array.
```
var doubleTrouble = n => console.log(n * 2);
R.forEach(doubleTrouble, [1, 2, 3, 4])//=>
>2
>4
>6
>8
[1, 2, 3, 4]
```

##head

Returns the first element of the given array or string.
```
R.head("dogs", "cats", "pigeons", "EDA")//=>["dogs"]
```

##indexOf

Returns the position of the first occurrence of an item in an array, or -1 if the item is not included in the array.
```
R.indexOf(21, [20, 21, 22, 23])//=>1
```

##insert

Inserts the supplied element into the list, at index index.
```
R.insert(3, 29, [20, 21, 22, 23])//=>[20, 21, 22, 29, 23]
```

##join

Returns a `string` made by inserting the `separator` between each `element` and concatenating all the elements into a single string.
```
R.join('-', [20, 21, 22, 23])//=>"20-21-22-23"
```

##length

Returns the number of elements in the array by returning list.length.
```
R.length([20, 21, 22, 23])//=>4
```

##map

Takes a funciton and a functor (element for the function to be applied to), and returns a new functor of the same shape. This can be applied to arrays or objects.
```
var double = x => x * 2;

R.map(double, [1, 2, 3]); //=> [2, 4, 6]

R.map(double, {x: 1, y: 2, z: 3}); //=> {x: 2, y: 4, z: 6}
```

##pluck

Returns a new array by 'plucking' the same named property off all objects in the array provided.
```
R.pluck('a')([{a: 1}, {a: 2}]);//=>[1,2]
```

##prepend

Returns a new list with the given element at the front, followed by the contents of the list.
```
R.prepend('fee', ['fi', 'fo', 'fum']); //=> ['fee', 'fi', 'fo', 'fum']
```

##reduce

Takes a function, accumulator value and an array, and returns a single value as a result.
```
var numbers = [1, 2, 3];
var add = (a, b) => a + b;

R.reduce(add, 10, numbers); //=> 16
```

##reject

The sister of `filter` - it returns an array of the items which are not specified in the function.
```
var isOdd = (n) => n % 2 === 1;

R.reject(isOdd, [1, 2, 3, 4]); //=> [2, 4]
```

##remove

Removes a sublist of array items starting at index provided in the first parameter, and lasting a count supplied in the second parameter, acting on the array in the third.

```
R.remove(2, 4, [1, 2, 3, 4, 5, 6, 7, 8])//=>[1, 2, 7, 8]
```

##repeat

Returns a fixed list of size `n` (second param) containing a specified identical value (first param).
```
R.repeat('hi', 5); //=> ['hi', 'hi', 'hi', 'hi', 'hi']
```

##slice

Returns an array between two specified indices. index 1 = param 1; index 2 = param 2; original array = param 3.
```
R.slice(1, 3, ['a', 'b', 'c', 'd']);        //=> ['b', 'c']
```

##tail

```
R.tail(["No", "learning", "at", "EDA"])//=>["learning", "at", "EDA"]
```

##take

Returns the first `n` elements of the given list, string, or transducer/transformer (or object with a take method).
```
R.take(2, ['foo', 'bar', 'baz']); //=> ['foo', 'bar']
```

##uniq

Returns a new list containing only one copy of each element in the original list.
```
R.uniq([1, 1, 2, 1]); //=> [1, 2]
```

##zip

Creates a new list out of the two supplied by pairing up equally-positioned items from both lists. The returned list is truncated to the length of the shorter of the two input lists

```
R.zip([1, 2, 3], ['a', 'b', 'c']); //=> [[1, 'a'], [2, 'b'], [3, 'c']]
```
```
R.zip(['a', 'b', 'c'], [1, 2, 3, 4]); //=> [[1, 'a'], [2, 'b'], [3, 'c']]]
```
