
# ydkjs - Up and Going

## Forward
Remember lighbulb moment - things went from blurry to crystal clear.
Truly master the concept to get the desired output.
Strieve to comprehend your code.

## Preface

JavaScript is the foundational technology of world's most widely available platform the web and the technology and capability of JavaScript has grown many orders of mangnitude.

Great deal of criticism as language due to its heritage and philosophy. (Java and JavaScript has nothing to do with each other).

JavaScript is much easier to get started and no one takes much effort to learn it's eccentricities like other languages C or Java for instance.

The JavaScript can be used without understanding, the understanding of the language is often never attained.

.

JavaScript has many surprises and frustations, thus ommiting them and learning only the "Good parts" should be considered as "The easy parts", "The safe parts" or even "Incomplete parts".

JavaScript is awesome. It's easy to learn partially, and much harder to learn completely (or even sufficiently). Don't blame the language for the lack of your understanding.

Embrace all javascript is and can do, with that knowledge, no technique, no framework, no buzzword acronym of the week will be beyond your understanding.

  

---

## Chapter 1: Intro Programming

**Program/ Source Code/ Code**

Special instructions to tell computer what task to execute

**Computer Language/ Syntax**

The rule for valid format and combination of instructions

**Statement**

A group of words, numbers and operators performing a specific task.

a = b * 2
- Variables
- Literals
- Operators

**Program Execution**

**Try it yourself**

console.log();

alert();

prompt();

**Values and Types**

Storing values in the program you require variables. JavaScript have different built-in types of values to store each of these so called primitive values. Example includes number, string, bolean etc. Suppose you want to show a number value on screen you first need to convert into string which is done implicitly by JavaScript. Though hJavaScript provides different utilities to provide conversion like Number(), String() etc.

Besides these primitive types like string, numbe, boolean, the lanague also provides arrays, objects, functions.

**Code Comments**
Programs should make sense when examined by humans, add sensible brief comments to code, interpreter/compiler always going to ignore them.

- Code without comments is sub-optimal.   
- Too many comments is  probably a sign of poorly written code.
- Comments should explain *why* not *what*

// Single Line Comment
/* Multi Line
Comment */

**Variables**
A symbol container storing program state values.

*Strong Typing/ Static Typing/ Type Enforcement*   
Programming language enforcing a vaiable to hold a specific type of value. Benefits include program correctness by preventing unintended value conversions.

*Dynamic typing / Weak Typing*
Programming language allows variable to hold any type of value at any time. Benefits its program flexibility according to program's logic flow.

JavaScript uses Dynamic approach meaning variable can hold any type value  without type enforcement at any time.

Declarations

    var amount; // Initialization ( notice we are not enforcing any type here )
    amount = 10; // Assignment
    amount = "$"+String(amount); // value can be coerced at any time( here explicit coercion)
    console.log(amount); // "$10"

Primary task of variables is to manage program state i.e., holds a running value i.e. is going to change with program flows.

*Constants*

    var PI = 3.1415926; // pre ES6 versions required constants to be declared as capitalized variables just to distinguish them from normal variables.
    const PI = 3.1415926' // ES6 version have dedicated type for constant, note initialization and assignment are required to be done at same time.  It prevents accidental changing of values.

Constants should be always declared at the program top; so it's convenient to change them at one place. If you tried to change the constant value after first declaration, your program would reject that change  ( or with strict mode fail with an error in case of variable kind declaration ).

The kind of "protection" against mistake is similar to static toying enforcement, that's why static typing makes other languages attractive.

**Blocks**
A group of series of statements together. In most languages its curly braces {}, Python have indentations for blocks.
The kind of standalone { ... } general block are valid but isn't commonly seen in JavaScript programs, typically it's attached to a control statement.
example  

    (condition){
    	...statements
    }

**Conditionals**
Decision expressions to control the program flows.
example  

    if(condition){
    	...statements
    } else if(condition){
    	...statements
    } else{
    	...statements
    }
.

    switch(_expression_) {  
    case  _x_:  
    _// code block  
    _break;  
    case  _y_:  
    _// code block  
    _break;  
    default:  
    //  _code block_  
    }

The condition or switch expression will always require a boolean value (even if your provide any other value or expression it will result in coerced to boolean value with the help of truthy/falsy set values).

**Loops**
Repeating a set of actions. The loop contains a condition and an attached block containing set of statements to be executed. The attached block executes when the conditional expression is satisfied. Each time the loop block executes, its called iteration.

    while(condition){
    	..statements
    }
.

    do{
    	..statements
    }while(condition)


For historical reasons, programming languages always count things in zero-based fashion. The index starts with 0.

    for(initialization clause; conditional clause; update clause){
    	..statements
    }

The loop until condition fails concept holds no matter what the form of loop.

**Funtions**
Reusable code blocks without repeated code writing.
A function is generally a named section of code that can be "called" by name, and the code inside it will be run each time.

function name([argument/s]){
	//..statements
	return value;  // default return is undefined;
}

**Scope**
Technically known as lexical scope.
Scope is basically a collection of variables and rules for how those variables are accessed by names. A variable name has to be unique within the same scope.  
Lexical scope rule says that code in one scope can access variables in the same scope or any scope outside it.  

    function one(){
    	var a = 1;
    	var b = 2;
    	var c = 45;
    	console.log("Inside one");
    	console.log(a);
    	console.log(b);
    	console.log("----------");
    
    	function two(){
    		var a = 3;
    		var b;
    		console.log("Inside two");
    		console.log(a);
    		console.log(b);
    		console.log("----------");
    
    		function three(){
    			console.log("Inside three");
    			console.log(a);
    			console.log(b);
    			console.log(c);
    			console.log("----------");			
    		}
    		three();
    	}
    	two();
    }
    one()

Practice 
There is absolute no substitute for practicing to learn programming. No part of reading, studying or learning can replace the code practicing.  


## Chapter 2: Intro JavaScript
Any good foundation is laid brick by brick; so don't expect you will understand everything at one go.

**Values and Types**  
JavaScript has types values, not typed variables. JavaScript have following built-in primitive types-  
- string  
- number
- boolean
- null and undefined
- object 
- symbol (new to ES6)

typeof operator to check the examine type of value in the variable.
 
 
| declaration | function | output | 
|--|--| -- |
| var a; | typeof a; | "undefined"
| a = "hello"; | typeof a; | "string"
| a = 42; | typeof a; | "number"
| a = true; | typeof a; | "booean"
| a = null; | typeof a; | "object"
| a = undefined; | typeof a; | "undefined"
| a = { name: 'jinkya'}; | typeof a; | "object"

The return type of typeof operator will always be one of these six(seven if consider symbol in ES6) string values. Only values in JavaScript have type; variables are just simply container for those values.
typeof null is interesting case, it should have returned null but returns object, it's a long standing bug and can never be fixed as a lot of websites in www are relying on these bugs.  

**Objects**
Compound value type where you can set keys and values for respective properties.  
Example -  

    var obj = {
    	a: "Hello, world",
    	b: 42,
    	c: true,
    	"store key": 4589
    }

Accessing properties  
- dot notation _ obj.a
- bracket notation _ obj["a"], obj["store key"]

Other types like like functions and arrays should be though as object subtype, specialized versions of the object type, instead of proper built-in types.  

**Arrays**  
An array is an object that holds values but in numerically indexed keys/positions.  

    var arr = [
    	"flag",
    	24,
    	true
    ];
    typeof arr; 	// "object"

Array always start with index 0, i.e., first element can be accessed with index 0.  

**Functions**  
typeof function returns "function" implying that function is a main type, but it should also be considered as subtype of objects, as you can use function attach properties very rarely in the program.
Example  
function foo() {
	return 42;
}
foo.bar = "hello world";
typeof foo;			// "function"
typeof foo();		// "number"
typeof foo.bar;		// "string"

**Built-in Type Methods**
The built-in types and subtypes have behaviours known as properties and methods.  

    var a = "Hello World";
    var b = 3.14159;
    a.length; // 11
    a.toUpperCase(); // "HELLO WORLD"
    b.toFixed(4); // 3.1416  

The *how* behind the toUpperCase is more complicated. While using the methods JavaScript engine simply puts String object wrapper, typically called native to access the method, this is boxing concept.  
Boxing is wrapping an object around a primitive value, unboxing is of course the reverse getting primitive value from the boxing object.  
For most parts you don't need to worry about or directly use the object wrapper forms of these values, prefer primitive value forms and JavaScript will take care of the rest.   

**Comparing Values**  
Two main types of value comparison - equality and inequality.  The result of any comparison is strictly boolean value(true or false) regardless of compared value type.  
	
	Coercion
Coercion comes in two forms - explicit and implicit.  
Explicit coercion is obvious from code that a conversion from one type to another will occur, whereas an implicit coercion will happen sometimes as non obvious side effects from some operations. Coercion is not evil and can be used to improve readability of code. 
explicit coercion  

    var a = "42";
    var b = Number(a);
    console.log(a);   // "42"
    console.log(b);   // 42

implicit coercion  

    var a = "42";
    var b = a * 1; 
    conosle.log(a);   // "42"
    console.log(b);  // 42
.
	
	Truthy and Falsy

Non boolean value coercion to a boolean.
The specific list of falsy values-  
- "" (empty string)
- 0, -0, NaN (invalid number)
- null, undefined
- false
Any value that is not in the falsy list is truthy. exalpes  
- "hello"
- 77
-  [], [1,2,3]
- {}
- function named(){ ... }

.

	Equality

Four equality operators 

    ==, ===, !=, !==
Do not confuse inequality(<,>,<=,>=) with non-equality.  
== check for value equality with coercion allowed. 
=== checks for value equality without allowing coercion.  
Generally consider as value checking AND value and type checking but that's partially true. 
Example  
var a ="42";  
var b =42;  
a == b;  // true  
a === b;   // false  
Some developers advocate use of === instead if == as it's more predictable, but this view is very shortsighted.  
[ES5 rules](http://www.ecma-international.org/ecma-262/5.1/)  
Simple boiled down rules-  
- If either value in the comparison is true/false, use ===.
- If either value in comparison is 0, "" or [], use ===.
- In all other cases, its safe to use ==.

If you are certain about values and == is safe, use it, otherwise use ===.
All the rules and properties we hold symmetrically for != and ! == .
For non-primitive values like objects ( including arrays and functions ) are actually held by reference. Thus the comparison will only check whether the references matches or not, not the underlying value.

    var a = [1,2,3];  
    var b = [1,2,3];  
    var c = "1,2,3";  
    
    console.log(a==c);  // true
    console.log(b==c);  //  true
    console.log(a==b);  // false

As you can see the array are simply coerced into strings to check the underlying values.  

	Inequlity
Relational comparison operators like <,>,<=,>=.
[ES 5 specifications]([https://www.ecma-international.org/ecma-262/5.1/#sec-11.8.5](https://www.ecma-international.org/ecma-262/5.1/#sec-11.8.5)) says NaN is neither greater or less than any other value.  
String comparison happens lexicographic ally (aka alphabetically as in dictionary).

    var a = 41;
    var b = "42";
    var c = "43";
    
    a < b;		// true
    b < c;		// true

.

    var a = 42;
    var b = "foo";
    
    a < b;		// false
    a > b;		// false
    a == b;		// false

.
**Variables**
Variable names (and even function or class names for that matter) must be valid. The strict and complete rules for indentifiers containing unicode characters are a little complex, but in case of typically ACII alphanumeric characters it's simple-
- An identifier must start with a-z, A-Z, $ or *_*. It can then contain any of alphanumeric character, no special characters except *_* and *$*. It can contain digits anywhere except the first index.  
- Certain words cannot be used as identifier names but as properties they are okay, known as *Reserved Words* namely true, false, null etc.  

**Function Scopes**  
var keyword is used to declare the a variable that will belong to the current function scope or global scope if declared outside.  

	Hoisting
Whenever a var appears inside a scope, its conceptually moved to the top of the scope and is accessible to the whole scope(also the unnamed function is moved at the top). Technically the process is more accurately explained with the code compilation. It's not good and common idea to rely on hoisting.  

    var a = 2;
    foo();					// works because `foo()`
    						// declaration is "hoisted"
    function foo() {
    	a = 3;
    	console.log( a );	// 3
    	var a;				// declaration is "hoisted"
    						// to the top of `foo()`
    }
    console.log( a );	// 2
.
	
	Nested Scopes
When you declare a variable; it's available inside that scope, as well as any child/inner/lower scope. If you try to access a variables value in a scope in which it is not available, a *ReferenceError* will be thrown. Trying to set a variable that hasn't been declared you will either create a global variable or get an error in 'strict mode'.  
Examples  

    function foo() {
    	var a = 1;
    	function bar() {
    		var b = 2;
    		function baz() {
    			var c = 3;
    			console.log( a, b, c );	// 1 2 3
    		}
    		baz();
    		console.log( a, b );		// 1 2
    	}
    	bar();
    	console.log( a );				// 1
    }
    foo();

.

    function foo() {
    	a = 1;	// `a` not formally declared
    }
    foo();
    a;			// 1 -- oops, auto global variable :(

.

    function foo(){
    	var a = 1;
    	if(a=1){
    		let a = 2;
    		console.log(a);  // 2
    	}
    	console.log(a);  // 1
    }

.

    function foo(){
    	var a = 1;
    	if(a=1){
    		var a = 2;
    		console.log(a);  // 2
    	}
    	console.log(a);  // 2
    }
var is function scoped while let is block scoped.

**Conditionals**
JavaScript provides conditional mechanisms like 
if..else if..else, switch case and ternary operator.
if else if syntax

    if(condition){
    	..statements
    } else if(condition){
    	..statements
    } else{
    	...statements
    }

switch case syntax (mind the break)

    switch(condition expression){
    case condition:
    	...statements;
    	break;
    case condition:
    	...statements;
    	break;
    default:
    	...statements
    }

Ternary Operator, the conditional operator

    condition ? execute_statements_if_condition_true : execute_statements_if_condition_false

**Strict Mode*
tbc...

## Chapter 3: Intro YDKJS

---

## Appendix A

---


## Footnotes

### Links
- [Mathis Bynes Blog]([https://mathiasbynens.be/notes](https://mathiasbynens.be/notes))

### left at
[link](https://github.com/getify/You-Dont-Know-JS/blob/1st-ed/up%20%26%20going/ch2.md#strict-mode)  
