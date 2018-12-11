## YDJS Scopes nd Closures
		Kyle Simpson

### What is Scope? 
A well defined set of rules is required for storing variables in some location and finding those variables at a later time maintaining state of the program.  
Despite fact that js falls under general category of 'dynamic' or interpreted' languages, it is infact a compiled language.  
It is _not_ compiled well in advance, as are many traditionally-compiled languages, nor are the results of compilation portable among various distributed systems.  
Compiled language three steps for rough 'compilation'
- Tokenizing/ Lexing  
  breaking up a string of characters into meaningful (to the language) chunks, called tokens.
		   
- Parsing  
  taking a stream (array) of tokens and turning it into a Abstract Syntax Tree
      var a = 2 ; 
     VariableDeclaration
	     Identifier  ( a )
	     Assignment Expression  
		     NumericLiteral (2)
		     
- Code generation  
  Process of taking AST and converting into executable code.

The JavaScript Engine is vastly complex than just those three steps like steps to optimize the performance of the execution, including collapsing redundant elements etc.  
JavaScript engines doesn't have the luxury of optimization as with others languages AOT, in JavaScript compilation happens in mere microseconds with all kind of tricks like JIT, lazy compile, hot re-compile etc.

#### Understanding Scope
		The Cast
Program process Character Cast
1. Engine - start to finish compilation and program execution. 
2. Compiler -   handles all the dirty work of parsing and code-generation
3. Scope  - ollects and maintains a look-up list of all the declared identifiers (variables), and enforces a strict set of rules as to how these are accessible to currently executing code.

		Back and Forth 
two distinct actions are taken for a variable assignment: First, _Compiler_ declares a variable (if not previously declared in the current scope), and second, when executing, _Engine_ looks up the variable in _Scope_ and assigns to it, if found.

		Compiler speaks
When an engine executes a code that compiler produces for it, it perform look up consulting scope.  
LHS lookup is done when a variable appears on the left hand side of the assignment operation.  
RHS lookup is done when a variable appears on the right hand side of the assignment operation.  
Think about it conceptually, its not mere besides the assignment operator, cause their are a lot of ways assignment can happen.  
Conceptually "who's the target of the assignment (LHS)" and "who's the source of the assignment (RHS)".  

		Engine/Scope Conversion  
[scope discussion ;)](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch1.md#enginescope-conversation)

#### Nested scope
if a variable cannot be found in the immediate scope, _Engine_ consults the next outer containing scope, continuing until found or until the outermost (aka, global) scope has been reached.  
[Another interesting conversation](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch1.md#nested-scope)  
		
		Building on metaphors  
![Build metaphors](https://raw.githubusercontent.com/getify/You-Dont-Know-JS/master/scope%20&%20closures/fig1.png)

		Errors  
two types of look-ups behave differently in the circumstance where the variable has not yet been declared.  
eg_  

		function foo(a) {
			console.log( a + b );  // RHS lookup _ ReferenceError
			b = a;	// without strict mode creates undefined*
		}
		
		foo( 2 );
*_"No, there wasn't one before, but I was helpful and created one for you."_

Strict mode from ES5, disallows automatic/implicit global variable creation.  
`ReferenceError` is _Scope_ resolution-failure related, whereas `TypeError` implies that _Scope_ resolution was successful, but that there was an illegal/impossible action attempted against the result.  


### Lexical Scope  

### Function vs block Scope  

### Hoisting  

### Scope Closures  

### footnote
1. [js compiled or interpretated](https://softwareengineering.stackexchange.com/questions/138521/is-javascript-interpreted-by-design)
2. 
