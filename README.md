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

















































