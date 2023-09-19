# Javascript

## Introduction
1. Javascript can change HTML contents
   ```js
   document.getElementbyId("demo").innerHTML = "Hello World";
   ```
   > Single and double quote are both fine
2. Javascript can change HTML attr values
   ```js
   document.getElementbyId("myImage").src = "on.jpg";
   ```
3. Javascript can change HTML styles (CSS)
   ```js
   document.getElementbyId("demo").style.fontSize = "35px";
   ```

## Where to put script?
You can place **ANY** number of scripts in an HTML document.

Scripts can be placed in the <body>, or in the <head> section of an HTML page, or in both.
> Placing scripts at the bottom of the <body> element improves the display speed, because script interpretation slows down the display.
> 
> Cached External JavaScript files can speed up page loads

## JS Output
JavaScript can "display" data in different ways:

* Writing into an HTML element, using `innerHTML`.
* Writing into the HTML output using `document.write()`.
  > Using `document.write()` after an HTML document is loaded, will delete all existing HTML only for testing
* Writing into an alert box, using `window.alert()`.
* Writing into the browser console, using `console.log()`.

> The JS `print()` is to print the content of the current window

## JS Statements
For best readability, programmers often like to avoid code lines longer than 80 characters.\
If a JavaScript statement does not fit on one line, the best place to break it is after an operator

## JS Comments
```js
// Single line comment
/*
    Multi-line comment
*/
```

## JS Identifiers
A JavaScript name must begin with:

* A letter (A-Z or a-z)
* A dollar sign ($)
* Or an underscore (_)

JavaScript programmers tend to use camel case that starts with a lowercase letter:

JavaScript uses the Unicode character set.

## JS Variables
When to Use var, let, or const?

1. Always declare variables

2. Always use const if the value should not be changed

3. Always use const if the type should not be changed (Arrays and Objects)

4. Only use let if you can't use const

5. Only use var if you MUST support old browsers.

```js
let carName
```

After defining a variable it become `undefined`

```js
let person = "John Doe", carName = "Volvo", price = 200;
```
Can declare many variables in one statement
```js
let person = "John Doe",
carName = "Volvo",
price = 200;
```
Or it can span multiple lines

> If you re-declare a JavaScript variable declared with var, it will not lose its value.
```js
let x = "5" + 2 + 3; // x = "523"
let x = 2 + 3 + "5"; // x = "55"
```
If you put a number in quotes, the rest of the numbers will be treated as strings, and concatenated.

>Using the dollar sign is not very common in JavaScript, but professional programmers often use it as an alias for the main function in a JavaScript library.

>In the JavaScript library jQuery, for instance, the main function $ is used to select HTML elements. In jQuery $("p"); means "select all p elements".

>Using the underscore is not very common in JavaScript, but a convention among professional programmers is to use it as an alias for "private (hidden)" variables.

## JS let

> let is introduced in ES6(2015)  

Variables defined with let **cannot** be redeclared.

```js
let x = "John Doe";
let x = 0; // Can not do this
```

```js
var x = "John Doe";
var x = 0; // can do
```

### Block Scope
**Variables defined with let have Block Scope**

Before ES6 (2015), JavaScript had Global Scope and Function Scope.

ES6 introduced two important new JavaScript keywords: let and const.

These two keywords provide Block Scope in JavaScript.

Variables declared with `let` inside a { } block **CANNOT** be accessed from outside the block:

Variables declared with the `var` keyword can NOT have block scope.

Variables declared inside a { } block **CAN** be accessed from outside the block.

- [ ] what is the point of block?


```js
var x = 2;   // Allowed
let x = 3;   // Not allowed

{
let x = 2;   // Allowed
let x = 3;   // Not allowed
}

{
let x = 2;   // Allowed
var x = 3;   // Not allowed ????
}
```
Redeclaring a JavaScript variable with var is allowed anywhere in a program\

With let, redeclaring a variable in the same block is NOT allowed\

Redeclaring a variable with let, in another block, IS allowed


### Let Hoisting
Variables defined with var are hoisted to the top and can be initialized at any time.

Meaning: You can use the variable before it is declared:

Variables defined with let are also hoisted to the top of the block, but not initialized.

Meaning: Using a let variable before it is declared will result in a ReferenceError:

## JS const

The const keyword was introduced in ES6 (2015)

Variables defined with const cannot be **Redeclared**

Variables defined with const cannot be **Reassigned**

Variables defined with const have **Block Scope**

JavaScript const variables **MUST** be assigned a value when they are declared:

**Use const when you declare:**

* A new Array
* A new Object
* A new Function
* A new RegExp

The keyword const is a little misleading. It does not define a constant value. It defines a constant reference to a value.


Because of this you can NOT:

* Reassign a constant value
* Reassign a constant array
* Reassign a constant object

But you CAN:

- Change the elements of constant array
- Change the properties of constant object

```js
// You can create a constant array:
const cars = ["Saab", "Volvo", "BMW"];

// You can change an element:
cars[0] = "Toyota";

// You can add an element:
cars.push("Audi");
```

```js
const cars = ["Saab", "Volvo", "BMW"];

cars = ["Toyota", "Volvo", "Audi"];  
// TypeError: Attempted to assign to readonly property.
``` 
```js
const car = {type:"Fiat", model:"500", color:"white"};
// You can change a property:
car.color = "red";

// You can add a property:
car.owner = "Johnson";
```

## JS Operators
Operator|Description
|-|-
`/` | divide
`*` | multiply
`++` | increment
`--` |decrement
`===`|equal value & type
`!==`|not equal val or not equal type
`?`|ternary <br>`variablename = (condition) ? value1:value2 `
`&&`|logical and
`\|\|`|logical or
`typeof`|return type
`instanceof`|true if instance of
`<<`|left shift
`>>>`|unsigned right shift
`>>`|right shift
`??=`|  Nullish coalescing assignment <br> If the first value is undefined or null, the second value is assigned.(ES2020)

## JS Data Types
JS has 8 data types
1. String
2. Number
3. Bigint
4. Boolean
5. Undefined
6. Null
7. Symbol
8. Object

The Object Datatype
The object data type can contain:

1. An object
2. An array
3. A date

**JavaScript Types are Dynamic**
```js
let x;       // Now x is undefined
x = 5;       // Now x is a Number
x = "John";  // Now x is a String
```

All JavaScript numbers are stored as decimal numbers (floating point).

Extra large or extra small numbers can be written with scientific (exponential) notation

> Most programming languages have many number types:

>Whole numbers (integers):
byte (8-bit), short (16-bit), int (32-bit), long (64-bit)

>Real numbers (floating-point):
float (32-bit), double (64-bit).

Javascript numbers are always one type:
double (64-bit floating point).

JavaScript BigInt is a new datatype (ES2020) that can be used to store integer values that are too big to be represented by a normal JavaScript Number.

## JS function

The () Operator calls the function

## JS Objects
### Declare  
```js
const car = {type:"fiat", price:10000}; // define with a object literal 
```

### Accessing Properties
```js
object.propertyName;
object["propertyName"]; // both are ok
```

### Declaring objects with methods
```js
const person = {
   firstName: "John",
   lastName: "Doe",
   age: 20,
   fullName: function() {
      return this.firstName + " " + this.lastName;
   }
};
```

### Keyword `this`
`this` is a keyword not a variable, cannot change its value

it points to different entities in different context:
1. in object methods, to the object
2. in function, global object, `undefined` if in strict mode
3. in event, the **element** received the event
4. alone, global object
5. in functions like `call()` `apply()`, anything

### Keyword `new`
Do not use `new` to declare Strings, Booleans and Numbers, slow down the code

## JS Events
Events are things that happens to HTML elements  
Event handlers are HTML attributes being JS code that react to events

### Common Events:
1. `onload`
2. `onclick`
3. `onchange`
4. `onmouseover`
5. `onmouseout`
6. `onkeydown`

## JS Strings

### String Length
```js
let l = text.length;
```

### Escape Character
can include " inside of a string literal quoted by ' but a better solution is:\
`\"` `\\` `\'`

`\b \v \r \f \t \n` are for typewritters

### Break long strings
```js
let longStr = "aaaaaaaaaaaaaaaaa" +
"bbbbb"
```

### Strings as Objects
strings can also be defined as objects

Comparing two JavaScript objects always returns **False**.


### Extract String
1. `slice(start, end)`
   end not included
2. `slice(start)`
   if negative, count backwards
   ```js
   "123456".slice(-3) == "456"
   "123456".slice(-3, -2) == "4"
   ```
3. `substring(start, end)`
   similar to slice(), but negative values treated as 0
4. `substr(start, len)`
   similar, but second arg is len, longer len is allowed

### String Replace
1. `replace(txt1, txt2)`
   return a **NEW** string\
   case sensitive by default\
   on replaces first occurence by default
   ```js
   let string = "abc ABC";
   string.replace("abc","efg");
   string.replace(/abc/i, "efg") // insensitive
   string.replace(/abc/g, "efg") // global match
   string.replace(/abc/gi, "efg")
   ```
2. `replaceAll()`
   similar, but `/g` flag must be set using regExp o/w TypeError

### Convert
`toUpperCase()` `toLowerCase()`

### Concatenaete
`concat()`
```js
text = "Hello" + " " + "World!";
text = "Hello".concat(" ", "World!"); // same
```

**All string methods produces a new string, formally Strings are immutable**

### Trim
`trim()` removes white spaces from both sides\
`trimStart()` only from the start\
`trimEnd()` from the back

### Padding
`padStart()`\
`padEnd()`
```js
"5".padStart(5,"0"); // pad with "0" until len=5
```

> `n.toString()` before using these methods


### Extract Characters
1. `charAt(index)`
2. `charCodeAt(index)` returns a UTF-16 code (an integer between 0 and 65535).
3. `[]`\
   1. make strings look like arrays
   2. `string[0] = "A"` no error but does not work
   3. `undefined` if not found, `charAt()` returns `""`

### Convert to Array
```js
string.split(","); // split on commas
string.split(""); // to array of characters
string.split(); // become the first element of the array
```


### String Search
`indexOf(str)` returns pos of the **FIRST** occurrence  
`lastIndexOf(str)` **LAST** occurrence

* Both return -1 if not found
* Both methods accept a second parameter as the starting position for the search:

```js
"012345678".lastIndexOf("678", 6) == 6;
// does not have to be after the last char
```

`search(str)`
similar to `indexOf(str)`
but:  
- cannot take a 2nd parameter
- can take a regExp

`match()` returns an array of matchs, o/w. `null`
```js
"aaaaA".match("aa"); // ["aa"]
"aaaaA".match(/aa/); // ["aa"]
"aaaaA".match(/aa/g); // ["aa"]
"aaaaA".match(/aa/i); // ["aa"]
"aaaaA".match(/aa/gi); //["aa", "aa"]
```

`matchAll()` returns an iterator of ALL occurences if matched o/w `null`

If the parameter is a regular expression, the global flag (g) **must** be set o/w. TypeError

`includes()` true if contains
Second parameter is starting position if negative search the whole string

`startsWith(str,pos)`  
`endsWith(str,pos)`

### Template Literals

```js
let text = `He's often called "Johnny"`;
let text =
`The quick
brown fox
jumps over
the lazy dog`; muiltiline string
```

```js
let firstName = "John";
let lastName = "Doe";
let text = `Welcome ${firstName}, ${lastName}!`; // string interpolation
```

## JS Numbers
Javascript numbers are always one type:
double (64-bit floating point). 
Mantissa 0-51, Exponent 52-62, Sign 63

**Integer are accurate up to 15 digits**
**Decimal are accurate up to 17 digits**

### Floating Precision
```js
let x = 0.2 + 0.1 // 0.30000000000000004
```

helps to multiply by 10 then divide by 10
or use the libraries `decimal.js` or `big.js`

```js
let z = "The result is: " + 10 + 20; // The result is: 1020
```

### Numeric Strings
Javascript will try to convert strings to numbers in numeric operations

```js
let x = "100"
let y = "10"
let z = x / y; // z = 10
z = x - y;
z = x * y;
z = x + y; // does not work
```

### NaN = Not a Number
Trying to do arithmetic with a non-numeric string will result in NaN (Not a Number):
```js
100 / "Apple" == NaN;
typeof(100 / "Apple") = NaN;
isNaN(100 / "Apple") == 1;
NaN + 5 == NaN;
NaN + "5" = "NaN5";
```

### Infinity
Infinity(or -Infinity)

1. returned when arithmetic overflows
2. returned when division by 0
3. is of type `number`

### Hexadecimal
preceded by `0x`

> octal number are precedied by `0` in some js versions

can use the toString() to output number from base 2 to base 36
```js
let number = 32;
number.toString(2) == 100000;
```

### Big