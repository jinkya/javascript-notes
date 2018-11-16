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
Javascript Patterns by Stoyan Stefanov(again a bit old but rigorous look at js design patterns)  

MDN ( defacto documentation of js aside from specifications itself.)

https://github.com/rwldrn/idiomatic.js ( coding style )

http://www.ecma-international.org/ecma-262/5.1/ ( provided algorithm pseudo ode for better unedrstanding of js specs )

js is going to evolve on a regular basis( mostly yearly ) 

Browsers aren't waiting for specifications.
Settles down in feature mode in the updated versions of browsers long before official specification based on proposal only.
Use transpilers to be backward compatible eg_ babel.js
New specifications not only make the code easier to write but also significat;y easier to maintain.
Don't hesitate to use the new speifications leave it for transpilers.

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

typeof the value contained by the variable !!

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

### Coercion
#### 

### Implicit vs Explicit Coercion
#### 

