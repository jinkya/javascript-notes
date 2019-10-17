# ydkjs Types and Grammar

## Foreword
## Preface
## Chapter 1: Types
**A type by any other name** 
[ES5.1](http://www.ecma-international.org/ecma-262/5.1/) specifications says
Algorithms within this specification manipulate values each of which has an associated type. The possible value types are exactly those defined in this clause. Types are further sub classified into ECMAScript language types and specification types.
Strongly/Static Typed Language developer may object to this use of type in Dynamic type lanaguage and argue it can be said "tags" or "subtypes".
A rough definition should be A type is an intrinsic and built-in set of characteristics that uniquely identifies the behavior of particular value and distinguishes it from other values, both to engine and developers.
If both engine and developer treat 42 and "42" differently then both these values have different types.
** A type by any other name**
Proper understanding of each type and its intrinsic behavior is essential for handeling coercion occuring in program.
Coercion can happen implicitly and explicitly. Implicit coercion can give strange and unexpected results, thus better grisp on types and values is required.


**Built-in Types**

**Values as Types**
JavaScript defines seven built-in types
- null
- undefined
- number
- string
- boolean
- object
- symbol (added in ES6)

All the datatypes are known as primitives except object. (Primitives ahve no properties, the length property applied is actually first coerced into String Object)

The typeof operator gives the type of the value

typeof undefined    === "undefined"
typeof true         === "boolean"
typeof 77 	    === "number"
typeof "77"         === "string"
typeof {life: 77}   === "object"
typeof Symbol()     === "symbol"

The return type is always of type string ;0
A [buggy](https://camo.githubusercontent.com/69910a60d3302b41dc333aa7e9cc52e2c657bb33/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f6e774f42762e706e67) feature which is never going to fixed is 
typeof null = "object"

null value checker
var a = null;
(!a && typeof a === "object"); // true

typeof function(){ ... } => "function";

Arrays and functions should be considered as subtypes of objects
A function is refered to as a "callable object" an object that has [[Call]] property allowing it to be invoked.
function a(b,c){ ... }
a.length; // 2
typeof [1,2,3] === "object";

	undefined vs "undeclared"
Undefined = A variable which is declared in the accessible scope, but at the moment has no value in it. 
Undeclared = A variable that is not formally declared in the variable.

var a;
console.log(a);  // undefined
console.log(b);  // ReferenceError: b is not defined yet.  

The typeof returns "undefined" even for the undeclared variables. 
var a;
typeof a;  // "undefined"
typeof b;  // "undefined"
Special safety guard behavior of the typeof throws no error after the execution.

	typeof undeclared
Avoiding global namespaces is considered to be ideal but not the case in practicality. With the help of ES6 modules, it will eventually become a reality.
Imagine having a debug mode variable in the project, DEBUG, which starts debugging,
if(DEBUG){
	console.log('Debugging started.');
}
This will throw an error if the debug is not declared, thus use
if(typeof DEBUG !== "undefined"){
	console.log('Debugging started.');
}
atob confusion

Another way to check against global variable without the type safety guard feature is checking if it's part of global variable i.e., window object.

if(window.DEBUG){
	//...
}
if(!window.DEBUG){
	//...
}

But it can be ambiguous sometimes as different JavaScript environments have different global variables (nodejs have global and browsers have window)

Not only for global variables, but it can also be used in other utilities, example-
function doSomethingCool(){
	var helper = 
	( typeof FeatureABC !== "undefined" ) ? FeatureABC : function() { //... }

	var val = helper();
}
or dependency injection pattern
function doSomethingCool(FeatureABC){
	var helper = FeatureABC || function(){ //... }
	var val = helper();
}

## Chapter 2: Values
Arrays, Strings and numbers are the most basic building block of a program.
### Arrays
As compared to statically typed languages the array in JavaScript comprises of types of values of any type
var arr = [1, "2", [3,4]]
a.length;  // 3
a[0];  // 1
a[2][0];  // 3

The aray size is not requierd to be predefined.
var arr = [];
a.length;  //0

Using delete on an array will remove that slot from the array, but even removing the final element it will not update the length property.
The sparse array
var a = [];
a[0] = 1;
a[2] = 3;
a[1];  //undefined
a.length; // 3
The created parsed array may have undefined inserted automatically, but it create unexpected behavior. Try to iterate with forEach().

Though array's are numerically indexed, as they are objects they can also have properties but hese don't count towards the length.
A gotcha to be aware about is that the string values are tried to be coerced into base 10 number.
var a = [];
a[0] = 1;
a["foobar"] = "hoo"
a["12"] = 42; //This will create element 42 at 12th index position.

Generally it's normal to use arrays for numerically indexed values and objects to store key property values.

**Array Likes**
Operations to convert a array like structure into true array so we can utilize the array ultilities like indexOf(), concat() etc.
One way to borrow slice
Tip: arguments is deprecated as of ES6
function foo(){
	var arr = Array.prototype.slice.call(arguments);
	arr.push("foo");
	console.log(arr);
}	
Other way ES6 Utility Array.from(...)
var arr = Array.from(arguments);

### Strings
Strings are not just array of characters. They might have shallow resemblance having a length property, concat(...) and idnexOf(...)
var a = "foo";
var b = ['f','o','o'];

a.length;  // 3
b.length;  // 3
a.indexOf("o");  // 1
b.indexOf("o");  // 1
var c = a.concat("bar");
var d = b.concat(['b','a','r']);

But the strings aren't just array of characters.
a[1] = "O";
b[1] = "O";
a;  // 'foo'
b;  // ['f','o','O']
Strings are immutable while arrays are mutable.
The a[1] approach is also not much valid (was not supporte din older IE but now do), the charAt(...) is more proper.

Further consequence of immutablity is string operations returns a new copy for most modifying functions, while array changes in-place.

c = a.toUpperCase();
a == c; // false;
console.log(a);  // 'foo'
console.log(c);  // 'FOO'

Many of the arrays useful methods are not directly available for the string, we can borrow non mutation array methods against string-
a.join();  // undefined
a.map();  // undefined

var c = Array.prototype.join.call(a, '-');  // "f-o-o"
var d = Array.prototype.map.call(a, function(v){
	return v.toUpperCase().join('.');
});  // 'F.O.O.'

Reverse a string (a js interview trivia question)
a.reverse(); //undefined
b.reverse(); // ['o','o','f']

Borrowing doesn't wok here with array mutators as Array.prototype.reverse.call(a) will not provide required output.

Workaround (aka hack), convert string into array, perform required operation and again convert into string.
var c = a.split("").reverse().join("");
But this method works for simple strings but strings containing special characters or unicode sequnces will result in error. 
More sophisticate libraries will be required for this approach.
Consult Mathias Bynens' work [Esrever](https://github.com/mathiasbynens/esrever).

If you require to do a lot of tasks that involve to treat string as an array of string better use array only and at the end 
just use join("") to convert into string.

### Numbers
JavaScript has just one numeric type "number" containing both ineger values and fractional decimal numbers. Like most modern languages javaScript is 
based on the 'IEEE 754' standard often called floating-point. JavaScript specifically uses double-precion format (aka 64 bit binary) standard.

Topic for another day - binary floating point storage into memory.
**Numeric Syntax**
JavaScript number literals are generally base-10 decimal literal.
var a = 75.6;
var b = 71;
Though, the leading and trailing 0 is optional, its good to use to avoid onfusion,
var c = .78
var d = 58.
As number's are outputes as base 10 decimals, the trailling zeros will be ommitted.
Very large or very small numbers will be converted into exponential formats.
var a = 5E10;
a; 50000000000;
a.toExponential();   // "5e+10"
var b = a*a;   // 2.5e+21
**Small Decimal Values**
**Safe Integer Ranges**
**Testing for Integers**
** 32 bit (Signed) Integers**

### Special Values
**The non-value values**
**Undefined**
**Special Numbers**
		
		The Not Number, Number
		Infinities
		Zeros
		
**Special Equality**

### Value vs Reference

## Chapter 3: 
## Chapter 4: 
## Chapter 5: 
## Appendix A: 
## Appendix B: 
