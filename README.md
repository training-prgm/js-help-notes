# js-help-notes

## let :

`let` allows you to declare block-level variables. The declared variable is available from the block it is enclosed in.

## const :

`const` allows you to declare variables whose values are never intended to change. The variable is available from the block it is declared in.

## var :

A variable declared with the `var` keyword is available from the written out function (as opposed to an anonymous function) it is declared in.

## while loop :

```
while (true) {
  // an infinite loop!
}
```

## do-while loop :

where you wish to ensure that the body of the loop is executed at least once.

```
do {
  input = get_input();
} while (inputIsNotValid(input));
```

## JavaScript's for :
```
for (var i = 0; i < 5; i++) {
  // Will execute 5 times
}
```

## JavaScript's for...of :
```
for (let value of array) {
  // do something with value
}
```

## JavaScript's for...in :
```
for (let property in object) {
  // do something with object property
}
```

## short-circuit logic :

The && and || operators use short-circuit logic, which means whether they will execute their second operand is dependent on the first. This is useful for checking for null objects before accessing their attributes.

`var name = o && o.getName();`

#### Or for caching values (when falsy values are invalid) :

`var name = cachedName || (cachedName = getName());`

## ternary operator :

`var allowed = (age > 18) ? 'yes' : 'no';`

#### `fall through` of switch statement (with/without break) :

```
switch (a) {
  case 1: // fallthrough
  case 2:
    eatIt();
    break;
  default:
    doNothing();
}
```

###### Note:

comparisons take place between the two using the `===` operator.

## Objects :

JavaScript objects can be thought of as simple collections of `name-value` pairs.

The "name" part is a JavaScript string, while the value can be any JavaScript value — including more objects. This allows you to build data structures of arbitrary complexity.

###### There are two basic ways to create an empty object :

```
var obj = new Object();`
var obj = {};
```

#### Object literal syntax :
```
var obj = {
  name: 'Carrot',
  for: 'Max', // 'for' is a reserved word, use '_for' instead.
  details: {
    color: 'orange',
    size: 12
  }
};
```

###### Attribute access :

```
obj.details.color; // orange
obj['details']['size']; // 12
```

#### object prototype :

`Person` and an instance of that prototype, `you`.
```
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Define an object
var you = new Person('You', 24); 
// We are creating a new person named "You" aged 24.
```

##### dot notation :
```
obj.name = 'Simon';
var name = obj.name;
```

##### bracket notation :
```
obj['name'] = 'Simon';
var name = obj['name'];
// can use a variable to define a key
var user = prompt('what is your key?')
obj[user] = prompt('what is its value?')
```

## Arrays :

##### creating arrays :
1.
```
var a = new Array();
a[0] = 'dog';
a[1] = 'cat';
a[2] = 'hen';
a.length; // 3
```
2.
```
var a = ['dog', 'cat', 'hen'];
a.length; // 3
```
3.
```
var a = ['dog', 'cat', 'hen'];
a[100] = 'fox';
a.length; // 101
```

###### If you query a non-existent array index, you'll get a value of undefined in return :
`typeof a[90]; // undefined`

##### With loops :
```
for (var i = 0; i < a.length; i++) {
  // Do something with a[i]
}
```

```
for (const currentValue of a) {
  // Do something with currentValue
}
```

Note : You could also iterate over an array using a `for...in` loop, however this does not iterate over the array elements, but the array indices. Furthermore, if someone added new properties to Array.prototype, they would also be iterated over by such a loop. Therefore this loop type is not recommended for arrays.

##### Using forEach() :

```
['dog', 'cat', 'hen'].forEach(function(currentValue, index, array) {
  // Do something with currentValue or array[index]
});
```
###### To append :
`a.push(item);`

##### Other lib methods:
###### toString()
Returns a string with the toString() of each element separated by commas.

###### toLocaleString()
Returns a string with the toLocaleString() of each element separated by commas.

###### concat(item1[, item2[, ...[, itemN]]])
Returns a new array with the items added on to it.

###### join(delimiter)
Converts the array to a string — with values delimited by the `delimiter` param

###### pop()
Removes and returns the last item.

###### push(item1, ..., itemN)
Appends items to the end of the array.

###### reverse()
Reverses the array.

###### shift()
Removes and returns the first item.

###### slice(start[, end])
Returns a sub-array.

###### splice(start, delcount[, item1[, ...[, itemN]]])
Lets you modify an array by deleting a section and replacing it with more items.

###### sort([cmpfn])
Takes an optional comparison function.

###### unshift(item1[, item2[, ...[, itemN]]])
Prepends items to the start of the array.

## Functions

###### Sample
Ex:
```
function add(x, y) {
  var total = x + y;
  return total;
}
```
###### Note:
1. The `return` statement can be used to return a value at any time, terminating the function. If no return statement is used (or an empty return with no value), JavaScript returns undefined.
2. calling a function without passing the parameters it expects, in which case they will be set to undefined.
3. functions have access to an additional variable inside their body called arguments, which is an array-like object holding all of the values passed to the function

###### Functions Arguments Object
Ex: 
```
function add() {
  var sum = 0;
  for (var i = 0, j = arguments.length; i < j; i++) {
    sum += arguments[i];
  }
  return sum;
}

add(2, 3, 4, 5); // 14
```

##### Functions Rest Parameters
Ex:
```
function sum(...theArgs) {
  return theArgs.reduce((previous, current) => {
    return previous + current;
  });
}

console.log(sum(1, 2, 3));
// expected output: 6

console.log(sum(1, 2, 3, 4));
// expected output: 10
```

A function's last parameter can be prefixed with ... which will cause all remaining (user supplied) arguments to be placed within a "standard" javascript array. Only the last parameter can be a "rest parameter".

Syntax:
```
function f(a, b, ...theArgs) {
  // ...
}
```

Ex:
```
function myFun(a, b, ...manyMoreArgs) {
  console.log("a", a); 
  console.log("b", b);
  console.log("manyMoreArgs", manyMoreArgs); 
}

myFun("one", "two", "three", "four", "five", "six");

// Console Output:
// a, one
// b, two
// manyMoreArgs, [three, four, five, six]
```

###### Differences between rest parameters and the arguments object:

1. Rest parameters are only the ones that haven't been given a separate name (i.e. formally defined in function expression), while the arguments object contains all arguments passed to the function;
2. The arguments object is not a real array, while rest parameters are Array instances, meaning methods like sort, map, forEach or pop can be applied on it directly;
3. The arguments object has additional functionality specific to itself (like the callee property).

###### From arguments to an array

```
// Before rest parameters, "arguments" could be converted to a normal array using:

function f(a, b) {

  var normalArray = Array.prototype.slice.call(arguments);
  // -- or --
  var normalArray = [].slice.call(arguments);
  // -- or --
  var normalArray = Array.from(arguments);

  var first = normalArray.shift(); // OK, gives the first argument
  var first = arguments.shift(); // ERROR (arguments is not a normal array)

}

// Now we can easily gain access to a normal array using a rest parameter

function f(...args) {
  var normalArray = args;
  var first = normalArray.shift(); // OK, gives the first argument
}
```

###### Destructuring rest parameters
Rest parameters can be destructured (arrays only), that means that their data can be unpacked into distinct variables.
Ex:
```
function add(...[a, b, c]) {
  return a + b + c;
}

add(1)          // NaN (b and c are undefined)
add(1, 2, 3)    // 6
add(1, 2, 3, 4) // 6 (the fourth parameter is not destructured)
```

###### Note:
JavaScript lets you call a function with an arbitrary array of arguments, using the apply() method of any function object.

```
add.apply(null, [2, 3, 4]); // 6
```
JavaScript lets you create anonymous functions and you can assign it to variables
```
var add = function(...[a, b, c]) {
  return a + b + c;
}
```
This is semantically equivalent to the function add() form.

It's extremely powerful, as it lets you put a full function definition anywhere that you would normally put an expression. This enables all sorts of clever tricks. Here's a way of "hiding" some local variables — like block scope in C:
```
var a = 1;
var b = 2;

(function() {
  var b = 3;
  a += b;
})();

a; // 4
b; // 2
```
JavaScript allows you to call functions recursively. This is particularly useful for dealing with tree structures, such as those found in the browser DOM.
```
function countChars(elm) {
  if (elm.nodeType == 3) { // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; child = elm.childNodes[i]; i++) {
    count += countChars(child);
  }
  return count;
}
```
This highlights a potential problem with anonymous functions: how do you call them recursively if they don't have a name? JavaScript lets you name function expressions for this.
```
var charsInBody = (function counter(elm) {
  if (elm.nodeType == 3) { // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; child = elm.childNodes[i]; i++) {
    count += counter(child);
  }
  return count;
})(document.body);
```

The name provided to a function expression as above is only available to the function's own scope. This allows more optimizations to be done by the engine and results in more readable code. The name also shows up in the debugger and some stack traces, which can save you time when debugging.

Note that JavaScript functions are themselves objects — like everything else in JavaScript — and you can add or change properties on them just like we've seen earlier in the Objects section.

## Spread syntax
Spread syntax allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

Ex:

`myFunction(...iterableObj);`

*For array literals or strings:*

`[...iterableObj, '4', 'five', 6];`

*For object literals (new in ECMAScript 2018):*

`let objClone = { ...obj };`

###### Spread in function calls

It is common to use Function.prototype.apply in cases where you want to use the elements of an array as arguments to a function.

```
function myFunction(x, y, z) { }
var args = [0, 1, 2];
myFunction.apply(null, args);
```
will also used like 
`myFunction(...args);`

Any argument in the argument list can use spread syntax and it can be used multiple times.

```
function myFunction(v, w, x, y, z) { }
var args = [0, 1];
myFunction(-1, ...args, 2, ...[3]);
```
##### Apply for new

When calling a constructor with new, it's not possible to directly use an array and apply (apply does a [[Call]] and not a [[Construct]]).
However, an array can be easily used with new thanks to spread syntax:
```
var dateFields = [1970, 0, 1];  // 1 Jan 1970
var d = new Date(...dateFields);
```
To use new with an array of parameters without spread syntax, you would have to do it indirectly through partial application:
```
function applyAndNew(constructor, args) {
   function partial () {
      return constructor.apply(this, args);
   };
   if (typeof constructor.prototype === "object") {
      partial.prototype = Object.create(constructor.prototype);
   }
   return partial;
}

function myConstructor () {
   console.log("arguments.length: " + arguments.length);
   console.log(arguments);
   this.prop1="val1";
   this.prop2="val2";
};

var myArguments = ["hi", "how", "are", "you", "mr", null];
var myConstructorWithArguments = applyAndNew(myConstructor, myArguments);

console.log(new myConstructorWithArguments);
// (internal log of myConstructor):           arguments.length: 6
// (internal log of myConstructor):           ["hi", "how", "are", "you", "mr", null]
// (log of "new myConstructorWithArguments"): {prop1: "val1", prop2: "val2"}
```
Creating using spread syntax:
```
console.log(new myConstructor(...myArguments));
// (internal log of myConstructor):           arguments.length: 6
// (internal log of myConstructor):           ["hi", "how", "are", "you", "mr", null]
// (log of "new myConstructorWithArguments"): {prop1: "val1", prop2: "val2"}
```
Fiddle link https://jsfiddle.net/re9f62mz/

##### Spread in array literals:
```
var parts = ['shoulders', 'knees']; 
var lyrics = ['head', ...parts, 'and', 'toes']; 
// ["head", "shoulders", "knees", "and", "toes"]
```
*copy an array*
```
var arr = [1, 2, 3];
var arr2 = [...arr]; // like arr.slice()
arr2.push(4); 

// arr2 becomes [1, 2, 3, 4]
// arr remains unaffected
```
*concat*
```
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
arr1 = [...arr1, ...arr2]; // arr1 is now [0, 1, 2, 3, 4, 5]
```

##### Spread in object literals
*merging objects (shorter than Object.assign)*
```
var obj1 = { foo: 'bar', x: 42 };
var obj2 = { foo: 'baz', y: 13 };

var clonedObj = { ...obj1 };
// Object { foo: "bar", x: 42 }

var mergedObj = { ...obj1, ...obj2 };
// Object { foo: "baz", x: 42, y: 13 }
```
Note that you cannot replace nor mimic the Object.assign() function.

##### Only for iterables
Spread syntax (other than in the case of spread properties) can be applied only to iterable objects:
```
var obj = {'key1': 'value1'};
var array = [...obj]; // TypeError: obj is not iterable
```
Note: When using spread syntax for function calls, be aware of the possibility of exceeding the JavaScript engine's argument length limit.
































Reference : https://stackoverflow.com/questions/111102/how-do-javascript-closures-work
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript
