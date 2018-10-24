

# ES 6 The right Parts
	The frontend masters
	by Kyle Simpson @getify

Javascript is rapidly evolving. Many people have differrent opiniated patterns, so this is just a opiniated guide. Code is not about instructing computer but communicating with human beings. More primary jobs are aimed at maintaining code ( Legacy code ). Readability mostly dependent upon familiarity. Read about [Automated code readability](https://web.eecs.umich.edu/~weimerw/p/weimer-tse2010-readability-preprint.pdf). 
- Imperative(how to do something) vs Declarative(what the output should be) Coding.
- ES6 - Adding more declarative forms (mostly a better way to communicate)
- It's not the case that _ is new _ ( like arrow is the new function )

### Arrow Functions
nice short concise syntactic form, really?

    function foo() {
	    return 2;
	}

is shorthanded to

    foo = ()=> 2;
    
- Arrow function Variations is kind of problem.
- Their is no variation for standard function syntax.

Arrow function variations

     =>3 ( headless arrow function is proposed. )
    () => 3 
    _ => 3 ( might hamper functionality if using underscore/ lodash lib )
    x => 3
    (...x) => 3
	(x,y) => 3 
	x => { try{ 3; } catch(e) {} } ( no more implied return, so need explicit return )
	x => ({ y:  x });		( returning an object )

- Syntactically anonymous function.
- Name inferencing will cause some hiccups.

	var foo = x => 3;
	foo.name;		//"foo"

Most all arrow functions will be arguments to some function calls.

Promises and this
	
	p.then( function(v){ return v.id; } )
	p.then( v => v.id; )
If v comes through as null or undefined js exception is thrown!
)

When to use Arrow function - A fun checklist
![when to use arrow function](https://raw.githubusercontent.com/getify/You-Dont-Know-JS/master/es6%20%26%20beyond/fig1.png)

When using lexical scoping for instances like var that = this, this is the place where arrow functions shine.

	var obj = {
	id: 42,
	foo: function foo() {
		var context = this;
		setTimeout(function(){
			// console.log(context.id);
				console.log(this.id);
		}.bind(this),100)
	}
	};

to

	var obj = {
	id: 42,
	foo: function foo() {
		var context = this;
		setTimeout(() => {
						console.log( this.id );
					},100)
		}
	};



### BlockScope
### Default values and the Gather/Spread Operator
### Destructuring
### Template Strings
### Symbols, Iterators, and Generators
