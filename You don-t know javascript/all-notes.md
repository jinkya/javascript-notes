===============================================================================
===============================================================================
1. Up and Going
2. Scopes and Closures
3. this and Object object
4. Types and Grammer
5. Async and Performance
6. ES6 and Beyond
===============================================================================
===============================================================================
Up and Going
-------------------------------------------------------------------------------
Foreword
.
.
- Remember "The lightbulb moment" after learning something.
- Learning new material is an exciting adventure, especially if you are looking to learn the subject efficiently.
- Truly master the material.
- The code isn’t just your job anymore, it’s your craft.
- Don't skim over the surface, but allow yourself to genuinely understand 
  the concepts you will be writing.
- The more you are exposed to JavaScript, the clearer it becomes. 
-------------------------------------------------------------------------------
Preface
.
.
- Cursing at the languages quirks is something we can probably all identify with!
- JavaScript has been a foundational technology that drives interactive experience around the content we consume.
- The technology and capability of JavaScript has grown many orders of magnitude in previous years.
- It is at the heart of the world's most widely available software platform: the web.
- As a language got a great deal of criticism, owing partly to its heritage but even more to its design philosophy.
- Brendan Eich once put it, "dumb kid brother" status ( mere accident of politics ). 
- Borrows concepts and syntax idioms from several languages
- While JavaScript is perhaps one of the easiest languages to get up and running with, its eccentricities make solid mastery of the language a vastly less common occurrence than in many other languages. Where it takes a pretty in-depth knowledge of a language like C or C++ to write a full-scale program, full-scale production JavaScript can, and often does, barely scratch the surface of what the language can do.
- True understanding is eluded (avoided) even for the most seasoned of JavaScript developers.
- JavaScript can be used without understanding, the understanding of the language is often never attained.
- Frustration in JavaScript, your response is to add it to the blacklist!!
-  "The Good Parts", I would implore you, dear reader, to instead consider it 
   the "The Easy Parts", "The Safe Parts", or even "The Incomplete Parts".
- Eschew(deliberately avoid using) the common advice to retreat when 
  the road gets rough.
- Journey down that bumpy "road less traveled" and embrace all that JavaScript 
  is and can do. With that knowledge, no technique, no framework, no popular 
  buzzword acronym of the week, will be beyond your understanding.
- A firm confidence in your understanding, not just of the theoretical, but 
  the practical "what you need to know" bits is driven by true understanding.
- You got code from others who've been burned by incomplete understanding'.
- Easy to learn partially, and much harder to learn completely (or even sufficiently).
-------------------------------------------------------------------------------
Chapter 1: Intro Programming
.
.
- The basic principles of programming at a very high level.
- Chapter 1 should be approached as a quick overview of the things you'll want to'learn more about and practice to get into programming. 
- Program/ Source Code/ Code is a set of special instructions to tell the computer what tasks to perform.
- Computer Language/ Syntax is the rules for valid format and combinations of 
  instructions. 
- Statements
  a group of words, numbers, and operators that performs a specific task
  a = b * 2;
  a,b - Variables - boxes you can store any of your stuff in.
  2 - a literal value
  = and * - Operators 
- Executing a Program 
  Running the program - tell the computer what to do.
  A special utility on the computer (either an interpreter or a compiler) is used to translate the code you write into commands a computer can understand.
  Interpreting the Code 
  Compiling the Code 
  Typically asserted that js is interpreted but not entirely accurate.
- Try it yourself
  Create a js file, include in HTML and run on the browser with 
  developer tool console
- about:blank in address bar and F12 / Ctr+Shift+I and Shift+Enter for next line.
  run some code
  a = 21;
  b = a * 2;
  console.log( b );
- Output 
  console.log(...) ( log, info, error, warn )
  alert(...) Popup
- Input 
  something = prompt('');	
- Operators
  Performing actions on variables and values. 
    Assignment =
    Math + - * / % and **(proposed power)
    Compound Assignment += -= *= /= 
    Increment/Decrement ++ --
    Object Property Access (.) as in console.log, obj.a obj['a'] 
    Equality ==(loose equal) ===(strict equals) !=(loose not-equals)
    Comparison <(less than) >(greater than) <= and >=
    Logical && ||

- Values and Types 
  - Number, Boolean, String
  - Literals eg_ 42, true, 'some string'

- Converting between Types
	- Explicit Coercion Facility _ Number(), String(), Boolean()
	- Controvertial with Implicit Coercion 
	  Same value in two diff representation "99.99"==99.99 // true
	  It was designedd to help but creates confusion
	  Sometimes called flaw in the design of the language

- Code Comments
	- Code is for the developer as it is for the compiler.
	- Program should make sense while examining, provide meaningful var names
	- Interpreter or compiler will always ignore the comments.
	- No universal rule but some points to consider
		- Code without comments is suboptimal.
		- Too many comments is a sign of poorly written code.
		- Comments can explain why not what, optionally what if its confusing
	- Two types
		- // Single Line Comment
		- /* Multi
			 Line Comment. */
.
- Variables
	- Symbolic container storing values varying over time as needed.
	- Languages can have enforcement for variable types.
		- Static typing ( type enforcement )
		- Dynamic Typing ( Weak typing )
	- Javascript uses Dynamic typing approach i.e. variable can hold any type of value without any type enforcement.

	var amount = 99.99; // var storing number
	amount = amount*2;
	console.log(amount); // implicitly coerce number to string to print
	amount = '$'+String(amount); // explicit coerce to string.
	console.log(amount);
	.
	- Primary purpose of variable _ managing program state
	- const before ES6 were declared in CAPITAL WORDS and _ for multiple words
	  Nothing special about it technically as it can be changed!
	  var TAX_RATE = 0.08; 
	  (21.2562).toFixed(3) // "21.256"
	- ES6 const 
	  const IN_CUR = 5.7;
	  IN_CUR = 8.9 // Uncaught TypeError: Assignment to const variable.
.
- Blocks
	- a curly brace pair of code statements { ... }
	- standalone block is valid but isn't commonly seen in JS programs.
	- a block statement does not need a semicolon(;) to conclude it.
- Conditionals
	- if(boolean_evaluating_expression){
				...
		} else if(boolean_evaluating_expression){
			...
		} else {
			...
		}
- Loops
	- Repeting set of actions (iterations) until a certain condition fails.
	- while(boolean_evaluating_expression){...}
	- do{} while(boolean_evaluating_expression);
	- break (get out of the loop) continue (escape to the next iteration.)
- Functions
	- Named section of code called by the name and passing some parameters
	- Function canoptionally take arguments(aka parameters) and optionally returns a value. The default return is undefined.
- Scope
	- Lexical scope is basically a collection of variables and the rules for how those variables can be accessed.
	- Nested scope.
-------------------------------------------------------------------------------
Chapter 2: Intro Javascript 
-------------------------------------------------------------------------------
- Values and Types
	- js has typed values not typed variables.
		- string
		- number
		- boolean
		- null and undefined
		- object
		- symbol (new to ES6)
	- typeof operator examining value type
		var a;
		typeof(a);      // "undefined"
		a = 'a string';
		typeof(a);		// "string"
		a = 42;
		typeof(a);      // "number"
		a = true;
		typeof(a);      // "boolean"
		a = null;
		typeof(a);      // "object"
		a = undefined    
		typeof(a);      // "undefined"
		a = { b: 'c' };
		typeof(a);      // "object"
	- typeof null = object is a bug that is never going to be fixed.
- Objects
	- a compund value with setting properties holding their own values.

		var obj = {
		a: 'hello',
		b: 42,
		c: true
		};

		obj['a']	// hello
		obj.b 		// 42
- Arrays
	- Object holding values with numerically indexed positions.

		var arr = [ 'a string', 12, true ]
		arr[0]	    // 'a string'
		arr[1]      // 12
		arr[2]	    // true
		arr.length  // 3
		typeof arr  // "object"

- Functions
	- another object subtype

	function foo(){
		console.log(12);
	}

	foo.bar = 'okay'

	console.log(typeof foo);   // "function"
	console.log(typeof(foo()));  // "undefined"
	console.log(typeof foo.bar); // "string"

- Built-In Type Methods
	- length, toUpperCase(), toFixed(..num..), Boxing like Number, Boolean etc.

- Comparing Values
	- Value comparison with equality and inequality resulting into strictly boolean value (true or false).

	- Coercion
		- Coercion 1. Explicit_ obvious from code, 2. Implicit_ non obvious side effect of some operations.
		- Explicit Coercion
			var a = "42";
			var b = Number(a);
			a;	// "42"
			b;	// 42
		- Implicit Coercion
			var a = "42";
			var b = a*1;
			a;	"42"
			b;	42
		- "Coercion is evil?" -> not evil nor have to be surprising but can be used to improve code readability.
	- Truthy and Falsy
		- When  a non boolean value is coerced into boolean it becomes truth or false with truthy and falsy natire of values.
		- Falsy values ( "", '', 0, -0, NaN, null, undefined, false )
		- Truthy values, values not in falsy list are Truthy ;) eg_
			"hello", 42, true etc.
	- Equality
		- Four equality Opearators ==, ===, !=, !==
		- == (check for value) (allows coercion) (loose equality)
		- === (check for value and type ) (no coercion) (strict equality)
		- Don't be advocate of ===, == is powerful tool if you take time to learn how it works ( http://www.ecma-international.org/ecma-262/5.1/ )
		- Cases in which === is required to be used
		  1. if either value in comparison could be true or false
		  2. if either values in comparison is (0, "", [])
		  3. In ALL OTHER CASES you can use the == operator.
		- Above cases hold symmetrically for non equality opearators.
		- Special care is required for non-primitive values like objects (including arrays and functions).
			 a = [1,2,3];
 			 b = [1,2,3];
 			 c = "1,2,3"
 			 .
			 a == c;  // true
			 b == c;  // true
			 a == b;  // false 
	- Inequality
		- Inequality operators <, >, <=, >=
		- If both values in inequality comparison are strings then comparison is made lexicographically.
		- If values are string and number then if string contains number bot hvalues will be coerced to number, else for potential different values types, the values will be coerced into NaN, thus resulting into false result of comparisons.
		- 
			var a =  41;
            var b = "42";
            var c = "43";
            a < b;  // true
            b < c;  // true
            .
            var a = 42;
			var b = "foo";
			a < b; // false
			a > b; // false
			a = b; // false
- Variables
	- Variable names must be valid identifiers. 
	- Strict and complete rules for valid char in identifiers is a little complex in non traditional char like Unicode. But for ASCII, rules are simple.
	- An identifier must start with a-z, A-Z , $ or _ 
	- Certain words can not be used as variable identifier ( Reserved words like for, in , null etc )

	- Function Scopes
		- var declaration belongs to the current function scope, or global scope if at top level otside function.
		- Hoisting
			- var declaration is moved to the top of its enclosing scope.
			- But do not rely on variable hoisting.
				var a = 2;
                foo();
                
                function foo(){
                  a = 3;
                  console.log(a);   // 3
                  var a;
                }
                
                console.log(a)  // 2
		- Nested Scopes
			- Inner scope have highest avaibility.

				function grand(){
				 var a = 1;
				 
				 function parent(){
				   var b = 2;
				   function child(){
				     var c = 3;
					 console.log(a,b,c)  // 1 2 3
				   }
				   child();
				   console.log(a,b);  // 1 2
				 }
				 parent();
				 console.log(a);  // 1
				}
				grand();
			- If var is not declared, the variable become global accessible everywhere!
			- ES6 lets you declare variable to individual scope instead of function scope.

			function foo(){
            	var a = 1;
            	if(true){
            		var b = 2;
            		let c= 3;
            	}
            	console.log(a,b,c) // Uncaught ReferenceError: c is not defined.
            }
            foo();
- Conditionals
	- if..else..if
	- switch
			switch(a) {
				case 2:
						// do something
						break;
				case 10:
						// do something
						break;
				default:
						// fallback to here

			switch(a):
				case 2:
				case 10:
						// do something
						break;
				case 42:
						// do something
						break;
				default:
						// fallback

			}
	- Ternary Operator
			(boolean_evaluating_expression) ? ( true evaluating statements ) : 
			( false evaluating statements )

- Strict Mode
	- ES5 added strict rules for certain behaviours.
	- Opt for individual function or an entire file
	- Disallow auto-global variable declaration from ommiting the var.
- Functions as values
	- A function itself can be a value that's assigned to variables, or passed to or returned from other functions.

	var foo = function(){			// anonymous function as no name
					// ...
				}
	var x   = function bar(){		// Named function expression
					// ...
				}

	- Immediately Invoked Function Expressions (IIFEs)
		(function IIFE(){...})();
- Closure
	- Remember and continue to access a function scope even once the function has finished running.
		function makeAddr(x){
				function add(y){
					return x+y;
				}
			return add;
		}

		var addOne = makeAdder(1);
		var addTen = makeAdder(10);
		
		console.log(addOne(5));
		console.log(addTen(5));

	- Modules
		- Most common usage of closures is module pattern.

		function User(){
			var usr, pwd;

			function doLogin(u,p){
				usr = u;
				pwd = p
				let result
				if(usr == 'ajinkya' && pwd == '123'){
					result = true;
				}else{
					result = false;
				}
				return result;
			}

			var publicAPI = {
				login: doLogin
			};
			return publicAPI
		};

		var ajinkya = User();
		ajinkya.login('ajinkya','123');	// true

		- User is a function, not a class to be instantiated, so without using new its just User().
		- The inner doLogin function has a closure over usr and pwd, meaning it will retain their access even after the User() function finishes running.
- this identifier
	- often this is related to 'object oriented pattern', but in JS this is a different mechanism
	- Inside function, this usually points to an object.
	- this does not refer to function itself (common misconception)
		function foo(){
			console.log(this.bar)
		}
		
		var bar = "globbal";
		
		var obj1 = {
			bar: "obj1",
			foo: foo
		}
		
		var obj2 = {
			bar: "obj2"
		}
		
		foo();          // "globbal"
		obj1.foo();     // "obj1"
		foo.call(obj2); // "obj2"
		new foo();      // undefined

- Prototypes
	- When you reference a property on an object, if that property doesn't exist, JavaScript will automatically use that object's internal prototype reference to find another object to look for the property on.

		var foo = {
		a: 42
		}
		
		var bar = Object.create(foo);
		
		bar.b = "hello world"
		
		foo; // {a:42}
		bar; // {b:"hello world"}
		
		bar.b; // "hello world"
		bar.a; // 42

- Old and New
	- Bring the newer javascript to the old browsers
	
	- Polyfilling 
		- ES6 introduced Number.isNaN(...) utility for buggy isNaN(...)
		- But its easy to polyfill this utility running on every browser

			if(!Number.isNaN){	// guards against applying polyfill def in ES6 browser
				Number.isNaN = function isNaN(x){
					return x != x;
				}
			}
		- Adhere to the specifications as strictly as possible.
		- Use trusted polyfills by ES5 shim and ES6 shim.

	- Transpiling
		- But thiers no way to polyfill new syntax, will give error as unrecognised to old js engines.
		- Tool for newer code to older code equivalent = transpiling = 
		tranforming + compiling
		- Why new if old is working
			- New syntax desifned to make code more readable and maintanable.
			- take advantage of browser performance optimization.
			- Helps TC39 committee testing new features for bugs.
			- eg
			  ES6 adds "default parameter values"
			  function foo(a=2){
			  	console.log(a);
				}
			  in older browser it required to transpile into
			  function foo(){
			  	var a = argument[0] !== (void 0) : arguments[0] : 2;
			  	console.log(a)
			}
		- Transpilers should be thought as JS development ecosystem and process part.
		- Good options _ Traceur, Babel etc.

- Non Javascript
	- A good chunk of code is not directly constrolled by js like DOM API
		var el = document.getElementByID(...)
		In new-generation browser, this layer may be part of JS only.
	- IO is browser object. i.e. console.log() and alert()	

----------------------------------------------------------------------------
Chapter 3: Intro YDKJS
- Learning all parts of js not just subset like 'the good parts'.
- Other language serious developers learns all of the language scenarios but in js case, most dev learns only the sufficient 'good parts'.

- Scopes and Closures _ critical understanding of lexical scope
- this and object prototypes _ dynamic bound of this keyword, take the red pill
- Types and Grammar _ Hihghly controvertial topic: type coercion, a fresh perspective
- Async and Performance _ callbacks, promises, aync, generators, webworker, asm.js, SIMD
- ES6 and beyond _ js is never going to stop evolving, new ES6 features.
----------------------------------------------------------------------------
Appendix A: Thanks
----------------------------------------------------------------------------


.
.
===============================================================================
===============================================================================
Scope and Closures
-------------------------------------------------------------------------------
Foreword
- Go into research mode for deep exploration
- desire to learn.
- Addict to 'why' question for all answers.
-------------------------------------------------------------------------------
Preface
- old one. 
-------------------------------------------------------------------------------
Chapter 1: What is Scope?
- Compiler Theory
	- js is general category of dynamic or interpreted languages, but infact a compiled language (not compiled in advance)
	- compilation process
		1. Tokenizing/Lexing _ beraking char string into chunks called tokens
		2. Parsing _ Turning token streams into nested element tree (Abstract SYntax Tree)
		3. Code genration _ Converting AST into executable code
	- The details of sys resource management by engine are much more complicated han above broad process.
	- js engine is vastly more complex as it doesn't get the luxury of AOT compilation. In js compilation occurs in most cases, mere microseconds before the code is executed. For fastest performance js uses all sort of tricks (like JIT, lazy compile and even hot-recompile)

- Understanding Scope
	- Think process in terms of conversation (think like Engine and friends)
		1. Engine _ start-to-finish compilation and execution of js program
		2. Compiler _ Handles dirty work of parsing and code generation
		3. Scope _ collect and maintains a look-up list of all declared variables and set strict rules for accessibility.

		var a =2;
		- Encountering var a, compiler asks scope if a variable a exists, if exists ignore declaration and move on. Else compiler aks scope to declare a new var a for that scope collection.
		- Compiler then produces the code for engine for execution, to handle a=2 assignment. The engine will ask scope if a is accessible to the current scope if not search elsewhere and assign it, if a is not found engine will throw an error.

	- The cast
	- Back and Forth
	- Compiler Speak
	- Engine/Scope Cpnversation
- Nested Scope
	- Building on metaphors
- Errors
- Review
-------------------------------------------------------------------------------
Chapter 2: Lexical Scope
- Lex time
- Look-ups
- Cheating Lexical
	- eval
	- with 
	- performance
- Review
-------------------------------------------------------------------------------
Chapter 3: Function vs Block Scope
- Scope from functions
- hiding in Plain Scope
	- Collision avoidance
		- Global "Namespaces"
		- Module management
- Function as scopes
	- Anonymous vs named
	- Invoking Function Expresion Immediately
- Blocks as scopes
	- with
	- try/catch
	- let
	- Garbage collection
	- let loops
	- const
- Review
-------------------------------------------------------------------------------
Chapter 4: Hoisting
- Chicken or the Egg
- Compiler strikes again
- Functions first
- Review
-------------------------------------------------------------------------------
Chapter 5: Scope Closures
- Enlightment
- Nitty Gritty
- Now I can see
	- CLosure
- Loops + Closure
	-Block scoping revisited
- Modules
	- Modern modules
	- Future modules
- Review
-------------------------------------------------------------------------------
Appendix A: Dynamic Scope
-------------------------------------------------------------------------------
Appendix B: Polyfilling Scope
-------------------------------------------------------------------------------
Appendix C: Lexical-this
-------------------------------------------------------------------------------
Appendix D: Thanks youz
-------------------------------------------------------------------------------


.
.
==================================================================================
==================================================================================
this and Object Prototype
----------------------------------------------------------------------------------
Foreword
----------------------------------------------------------------------------------
Preface
----------------------------------------------------------------------------------
Chapter 1:
----------------------------------------------------------------------------------
Chapter 2:
----------------------------------------------------------------------------------
Chapter 3:
----------------------------------------------------------------------------------
Chapter 4:
----------------------------------------------------------------------------------
Chapter 5:
----------------------------------------------------------------------------------
Chapter 6:
----------------------------------------------------------------------------------
Appendix A: ES6 Class
----------------------------------------------------------------------------------
Appendix B: Thanks
----------------------------------------------------------------------------------

.
.
==================================================================================
==================================================================================
Types and Grammer
----------------------------------------------------------------------------------
Foreword
----------------------------------------------------------------------------------
Preface
----------------------------------------------------------------------------------
Chapter :
----------------------------------------------------------------------------------
Chapter :
----------------------------------------------------------------------------------
Chapter :
----------------------------------------------------------------------------------
Chapter :
----------------------------------------------------------------------------------
Chapter :
----------------------------------------------------------------------------------
Appendix A:
----------------------------------------------------------------------------------
Appendix B:
----------------------------------------------------------------------------------

.
.
==================================================================================
==================================================================================
Async and Performance
----------------------------------------------------------------------------------
Foreword
----------------------------------------------------------------------------------
Preface
----------------------------------------------------------------------------------
Chapter 1: Asynchrony: Now and Later 
----------------------------------------------------------------------------------
Chapter 2: Callbacks 
----------------------------------------------------------------------------------
Chapter 3: Promises 
----------------------------------------------------------------------------------
Chapter 4: Generators 
----------------------------------------------------------------------------------
Chapter 5: Program Performance
----------------------------------------------------------------------------------
Chapter 6: Benchmarking and Tuning 
----------------------------------------------------------------------------------
Appendix A: Library: asynquence
----------------------------------------------------------------------------------
Appendix B: Advanced Async Patterns 
----------------------------------------------------------------------------------
Appendix C: Thanks
----------------------------------------------------------------------------------

.
.
==================================================================================
==================================================================================
ES6 and Beyond
----------------------------------------------------------------------------------
Foreword
----------------------------------------------------------------------------------
Preface
----------------------------------------------------------------------------------
Chapter 1: ES? Now and Future 
----------------------------------------------------------------------------------
Chapter 2: Syntax 
----------------------------------------------------------------------------------
Chapter 3: Organisation 
----------------------------------------------------------------------------------
Chapter 4: Async Control Flow 
----------------------------------------------------------------------------------
Chapter 5: Collections 
----------------------------------------------------------------------------------
Chapter 6: API Additions 
----------------------------------------------------------------------------------
Chapter 7: Meta Programming 
----------------------------------------------------------------------------------
Chapter 8: Thanks
----------------------------------------------------------------------------------
----------------------------------------------------------------------------------
==================================================================================
==================================================================================
