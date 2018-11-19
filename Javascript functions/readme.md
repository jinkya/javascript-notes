***
## Javascript Functions  
	Lynda 
	Ray Villalobos Lynda Course
	1 hour 25 min 
***
### Introduction

series of statements that are grouped together in a special package

Function Basics  
Defined with the function keyword  
Defining = Declaring  

Functions have to be defined or declared  
Function name is optional  
Function Parameters  
Function { Statements }  
The return statement  

Invoking the function  


***
### Getting Started

*Function declaration
Two ways

Traditional Declarations
function plus(a,b){
	return a+b;
}
plus(2,3);

Validity of the variable name http://goo.gl/M3f1V7


Defining Expressions ( / Anonymous Function )
var plus = function(a, b){
 return console.log(a+b);
};
plus(1,2)

Immediately Invoked Way
function(a,b){ return console.log(a+b)}(1,2)

*Invoking Functions Traditionally

4 ways
 Functions
 Methods
 Constructors
 Call and Appy Method

Invocation patterns
 Receive argumetns and this
 Invoking stops current execution
 plus(a,b)
 Traditional invocation ( this bound to global object )

function plus(a,b){
	return (
		console.log(a+b);
		console.log(this);
		console.log(arguments);
	)
}

***
### Function Invocation

*Using functions as objects
Invoking functions as methods which are property of an object.

Object - js Datatype, most flexible datatype  
eg
var info = {
	name: "Ajinkya",
	title: "ASE",
	links: [
        { blog: 'jinkya.io' },
        { twitter: 'followme.twitter.com' }
	]
}


var calc = {
	status: 'awesome',
	plus: function (a,b) {
		return (
				console.log(this);
				console.log(a+b);
				console.log(arguments);
				console.log(this.status);
				)
	}
}

calc.plus(2,2);

*

***
### Using Functions
***
### Conclusion
***
