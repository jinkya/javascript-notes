
## Functional Lite Javascript
    Kyle Simpson
    Lynda
    3 hours 9 min

***

### Pure Functions

#### Intro  
@getify
You don't know JavaScript
Mastering is continuous process  

#### Agenda  
- Pure Functions 
- Composition 
- Immutability 
- Closure 
- Recursion 
- List transformation (map) 
- List Exclusion (filter)
- List Composition (reduce) 
- List Iteration (forEach)

#### Side Effects  
Changing state of  program by calling a function.

	function foo(x) {
		y = x * 2;
		z = x * 3;
	}
	var y, z;
	foo(5);
	console.log(y);
	console.log(z);

foo is an impure function as its changing state of y and z forever.
The way some functional programmer make it pure again is to wrap another function aound it to contain all those side-effects within that function. And from outside that function appears pure. 
Pure at the highest level.


	function foo(x){
		y = y * x;
		z = y * z;
	}
	var y = 2, z = 3;

	foo(5);
	console.log(y); // 10
	console.log(z); // 15
	
	foo(5)
	console.log(y); // 50
	console.log(z); // 75



Pure: no side effect 
Pure function is a function that has no side effects, it operates entirely on its own variables, its own states, or any of the things passed to it.
Put entire state of program in to the function. 

	function bar(x,y,z) {
		foo(x);
		return [y, z];

	function foo(x){
			y = y * x;
			z = y * x;
		}
	}
	
	bar(5,2,3);    // [10, 15]
	bar(5,10,15);  // [50, 75]

#### Exercise 1  
Make a pure function `bar(..)` to wrap around `foo(..)`

	function foo(x) {
		y++;
		z =  * y;
	}

	var y = 5, z;

	foo(20);
	z;		  // 120
	foo(25);
	z;        // 175

#### Solution  
	function bar(x,y){
		var z;
		y = 5;
		foo(x);
		return [y,z];
	function foo(x){
			y++;
			z = x * y;
		}
	}
	
	bar(20,5);

***
### Composition and immutability

#### Mutual composition  
COmposition 
Taking output of one function and putting it directly as the input to another function. Instead of calling one function and then calling another function, we are going to call one function and its output is going to become at least part of the input for another function. And th eoutput of that function can be part of the input for another function. 

eg _ manual composition 

	function sum(x,y) {
		return x + y;
	}
	function mult(x,y) {
		return x*y;
	}
	sum(mult(3,4), 5);

AND 
	
	function sum(x,y) {
		return x + y;
	}
	function mult(x,y) {
		return x*y;
	}
	function multAndSum(x,y,z){
		return sum( mult(x,y), z);
	}
	multAndSum(3,4,5)

#### Composition utility  
Extrapolate compostion to a general sense. 
Find reusable patterns.

function sum(x,y) {
	return x+y;
}
function mult(x,y) {
	return x*y;
}
function compose2(fn1, fn2) {
	return function comp(){
		var args = [].slice.call(arguments);
		return fn2(
			fn1(args.shift(),args.shift()), args.shift()
		)
	}
}
var multAndSum = compose(mult, sum);
multAndSum(3,4,5);

#### Immutability  
var x = 2;
x++;		// allowed

const y = 3;
y++;		// not allowed

const z = [1,2,3];
z = 10;		// not allowed
z[0] = 10;	// allowed

const w = Object.freeze([4,5,6]); // shallow immutability, no deep down immutability
w = 10;		// not allowed
w[0] = 10;	// not allowed

Non ability to mutate 
const gives immutable values? false
It only gives immutable assignment/ imutable binding to a value. 

Primitives a re by definition immutable. 
const doesn't have to do anything with the mutable or immutable value anymore than var does.
var and const are controlling the binding of a variable to some paticular value.

const z is not declaring an immutable array, it is declaring an immutable variable called z bound to that particular array by reference.

For more sophisticate dimmutability their are lot of js libraries to use. 

#### Questions on Immutability  


***
### Closure and Recursion

#### Closure  
#### Exercise  
#### Solution  
#### Recursion  
#### Example  
#### Exercise  
#### Solution  

***
### List Operations  

#### List transformation  
#### List exclusion  
#### List composition  
#### List iteration  
***
