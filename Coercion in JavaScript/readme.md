
## Coercion in JavaScript

    Lynda
    Kyle Simpson
    3 hour 18 minutes

---
### Primitive types
#### Introduction
About author  
Kyle Simpson
@getify
http://getify.me
http://speakerdeck.com/getify

Created LABjs, grips(ejs), asynquence  
http://YouDontKnowJS.com

#### Additional Resources
High performance js by Nichlas Zakas(a bit out of date)  
Javascript Patterns by Stoyan Stefanov ( again a bit old but rigorous look at js design patterns. )  

MDN ( defacto documentation of js aside from specifications itself.)
Its javascript wikipedia, exhaustive documentation of javascript. Contribute to the community by checking and updating if found errors.

[Coding Styles](https://github.com/rwldrn/idiomatic.js)
[Algorithm pseudo code for better js specs understandings](http://www.ecma-international.org/ecma-262/5.1/)

javascript is going to evolve on a regular basis( mostly yearly ) 

Browsers aren't waiting for specifications.
They settles down in feature mode in the updated versions of browsers long before official specification based on proposal only.
Use transpilers to be backward compatible eg_ babel.js
New specifications not only make the code easier to write but also significantly easier to maintain.
Don't hesitate to use the new specifications, leave backward compatibility for transpilers.

#### Primitive Types
False assumption - js have no types - Academic Debates

- undefined
- String
- number
- boolean
- object
- function ( but its not defined as type in specs! )
- null ( it has a bug with it )

undefined is like the empty values and null is the empty object value. ( by specifications )

#### typeof
typeof foo;     // "undefined" - undeclared var
typeof "foo";   // "string"
typeof 123;     // "number"
typeof true;    // "boolean"
typeof { a:1 }; // "object"
typeof function() { alert(e); }; // "function"

typeof null    // "object"  ( problem with null )
( Brendan Eich himself clarified its a bug on twitter )
![Brendan Eich Twit](https://i.stack.imgur.com/nwOBv.png)

typeof means type of the value contained by the variable !!

undeclared and undefined are not same.
js does not have var type but value type 

Why they are not removing the bugs?
TC39 committee defined specification have browser vendors as their memeber and browsers oppose the removal as a lot of sites are utilizing the buggy features.
web compatibility reasons.
Browsers are at war for the market share and changing the fundamentally will break a lot ofsites.
Ratio 1/1000 site breaks, reject it. ( not confirmed )

typeof typeof 2 // "string"

#### Special values: NaN  
not a number ( should be a invalid number )
Infinity, -Infinity
null // a keyword
undefined(void) // identifier, a variable
+0, -0 ( IEEE 754 language like Ruby, Python etc. but hides the fact)

"a"/2   // NaN
typeof(NaN)  // "number"
isNaN(NaN)   // true
isNaN("foo") // true

ES utility to check NaN

	if(!Number.isNaN) {
		Number.isNaN = function(num) {
			return (
				typeof num === "number" && window.isNaN(num)
			)
		}
	}

#### Special Values: Negative Zero
	var foo = 0/-3
	foo === -0;        // true
	foo === 0;         // true
	0 === -0           // true
	(0/-3) === (0/3)   //true
	foo                // 0 ( in older browsers )
Same behaviour cannot be expected from all the developer consoles.

isNegative zero utility

	function isNeg0(x){
		return x===0 && (1/x)===-Infinity;
	}

ES6 : Object.is() ( But don't use it instead of === )
		
	Object.is("foo", NaN); // false
	Object.is(NaN, NaN)  // true
	Objet.is(0,-0);      // false
	Objet.is(-0,-0);      // true

#### Special Values: Quiz
! Variable is declared only once for a given scope.

	var baz = 2;
	typeof baz;   // "number"
	var baz;
	typeof baz    // "number"
	baz = null;
	typeof baz;    // "object"

	baz = "baz" * 3;
	baz;               // NaN
	typeof baz;        // "Number"

	baz = 1/0;        // Infinity
	baz;          
	typeof baz;       // "Number"

#### Natives
No perfect terminology
Native Types/ Native Objects ?
Natives are functions in addition to objects 
Native constructors? new String(), new Object()

Specifications doesn't apply to browser dev consoles!!!
Different browsers show different outputs!!!
Lot's of confusion.
An object wrapper has been constructed and wrapped around the primitive values by the browsers.

	var foo = new String("foo");   // String {"foo"}
	typeof foo;                    // object
	foo instanceof String          // true
	foo instanceof string          // nonsense!!! its an indenifier

	foo = String("foo");		// foo
	typeof foo;					// string

	foo = new Number(37);		// Number { 37 }
	typeof foo;					// object

	var foo = new Boolean(false)   // Boolean {false}
	if foo console.log("called");  // called		 
Try to avoid new.

String Number Boolean should be used for coercion.

	var foo;
	foo = new Array(1,2,3);  // new Aray(42)
	foo = [1,2,3];

	foo = new Object();
	foo.a = 1;
	foo.b = 2;
	foo.c = 3;

	foo = { a:1, b:2, c:3 };


	var foo;
	foo = new RegExp("a*b","g"); // Dynamic reg exp
	foo = /a*b/g; // Static reg exp (prefer this as its staic)
	foo = new Date();

---
### Coercion
Abstract Operations  
Conversion of one type to another. 

#### ToString Method
toString()
		
	null       "null"
	undefined  "undefined"
	true       "true"
	false      "false"
	3.1415     "3.1415"
	0          "0"
	-0         "0"    // a bit anomaly

// a lot anomaly - broken by design
	
	[]                 ""
	[1,2,3]            "1,2,3"
	[null,undefined]   ","
	[[[],[],[]],[]]    ",,,"
	[,,,,]             ",,," // trailing comma ignored

	{}     "[object Object]"
	{a:2}  "[object Object]"

#### ToNumber Method
	""        0 // Root of all coercion evil in JS
	"0"       0
	"-0"     -0
	" 009 "   9
	"3.1415"  3.1415
	"0."      0
	".0"      0
	"."       NaN
	"0xaf"    175 

	false      0
	true       1
	null       0
	undefined  NaN

ToNumber(object) => ToPrimitive(number) (hints) valueOf(), toString() => NaN

	[""]           0
	["0"]          0
	["-0"]        -0
	[null]         0
	[undefined]    0
	[1,2,3]        NaN
	[[[[]]]]       0

#### ToBoolean Method
ToBoolean abstract operation 
Specifications doesn't define falsy/ truthy.

	Falsy            Truthy
	""               whats not of left ;) really
	0,+0,-0			 "foo"
	null             23
	NaN              []
	false            true
	undefined        function(){...}


---
### Implicit vs Explicit Coercion
Explicit - it's obvious from the code that you're doing it. ( Explicit Coercion or Explicit type Conversion )

Implicit - Happens as a side effect of some other operation. Evil? not evil but quite uselful

#### Explicit coercion: Strings and numbers
string <---> number  

var foo = "123";
var baz = parseInt(foo,10); // base 10 no system
// Coercion and parsing are different.
baz;               // 123

baz = Number(foo);
baz;              // 123

baz = +foo;       // explicit? unary opeator form coerce anything to number (debatable point)
baz;              // 123

baz = 456;
foo = baz.toSting();
foo;                  // "456"
// boxing primitive value in js object wrapper form.
// subtle implicit coercion
// Implicit Boxing mechanism

foo = String(baz);
foo;                  // "456"

Most preferable forms are String() and Number()


#### Explicit coercion: Booleans
var foo = "123";
var baz = Boolean(foo);   // Explicit
baz;					// true

baz = !!foo;
baz;					// true

// explicitly implicit!
baz = foo? true : false;  // idioms coming from java
baz					      // true

side note
var now = +(new Date());
// now = Date.now();   // ES5 only! a preferable option
-----
sentinel values - values otherwise have no special value but we assign a special meaning to it.
var foo = "foo";
// ~N -> -(N+1)
if (~foo.inedxOf("f")){
	alert("Found it!");
}

Leaky abstraction coding like
indexOf returning -1.

-----
var now1 = new Date(); // "object" Fri Nov 16 2018 16:18:38 GMT+0530 (India Standard Time)

var now2 = Date.now(); // "number" 1542365340993

Hiding abstraction is basically impoving readability of the code.


#### Implicit Coercion: Strings and numbers
var foo = "123";
var baz = foo - 0;
baz;                 // 123

baz = foo - "0";
baz;                 // 123

baz = foo / 1;
baz;                 // 123

baz = 456;
foo = baz + "";
foo;                 // "456"

foo = baz - "";
foo;                 // 456


#### Implicit Coercion: Booleans
var foo = "123";

if(foo) { console.log("sure"); }   //yes

foo = 0;
if(foo){ console.log("sure"); }   //no

if(foo == false){ console.log("sure"); } // yes

var baz = foo || "foo";
baz;                      // "foo"

#### Double-equal issues


#### Implicit coercion: The bad parts


#### Implicit coercion: The safe parts


#### Double vs. triple equal


#### Helpful implicit coercion


#### Coercion resources and surprises


---

