
## JavaScript Classes

    Lynda
    Emmanuel Henri
    37 m 18 s

---
### Introduction  
#### Classes  
ES6 for better prorotype syntax.  
Syntactic sugar over prototypes.  
Classes changes get passed down.  
Classes aren't hoisted at top thus required to declare first to use it.  
Two ways to define - Class Declaration and Class Expression.  
Properties and Methods can be attached to methods.  
  
### Defining classes  
#### Class Definition
emmet plugin for the syntactic shortcuts.  
Install Live Server Plugin 
( Start a server with simple command - Shift Ctr P - Live Server Open - Browser).  

    class Car{
	constructor(doors, engine, color){
		this.doors  = doors;
		this.engine = engine;
		this.color  = color;
		}

	carStats(){
		return `This car has ${this.door} doors, 
        a ${this.engine} and ${this.color} color!`
		}
	}

	const cx5 = new Car(4, 'v8', 'grey');
	console.log(cx5);
	console.log(cx5.carStats());

#### Difference between Functions and Classes  
|Functions| Classes |
|--|--|
| Hoisted | Not Hoisted |
| Can be overwritten | Can't be overwritten( can be extended) |

When creating a reusable blueprint and also need functions create a class  
eg_ React Class Component  

	class Clock extends React.Component {
	render(){
		return (
			<div>
				<h1> Hello </h1>
				<h2> { this.props.date.toLocalTimeString() }. </h2>
			</div>
			)
		}
	}

When need to create a brand new function not requiring any specific property or method use function  
eg_ React Functional Component  

	function Welcome(props){
		return <h1> Hello, {props.name} </h1>;
	}

#### Hoisting  
Utilization of class instances before class definition throws a reference error.
Always define the class before using it.  
Function have different hoisting rules.  
  
#### strict mode (ES 5 )  
[Explore](https://mzl.la/1onrGsw)  
Make developer more aware about hoisting and other best practices adding throw away error at compilation.  
Also improves performance with review for better compilation.  
When declare a class it's automatically in strict mode.  
Also all its properties and methods.  
  
#### Static method and usage  
Static methods aren't accessible through instance of class but only through class itself.  
Created for Utility function that don't relate to instance of class.  
  
	class Car{
		constructor(doors, engine, color){
			this.doors  = doors;
			this.engine = engine;
			this.color  = color;
		}
		
	car Stats(){
		return `This car has ${this.doors}, a ${this.engine} engine and a beautiful ${this.color}!`;
		}

	static totalDoors(car1, car2){
		const doors1 = car1.doors;
		const doors2 = car2.doors;
		return doors1 + doors2;
	}
	}

	const car1 = new Car(4, 'v7', 'white');
	const car2 = new Car(2, 'v5', 'blue');
	console.log(car1);
	console.log(car1.carStats());
	console.log(Car.totalDoors(car1, car2));

#### Prototype Methods explained  
Class is just syntactical sugar over prototype.  
Inherits the methods of prototype.  
console.log(car1);  
_proto_ { constructor, carStats( multiple properties bindings ) }  

    class Car{
		constructor(doors, engine, color){
			this.doors  = doors;
			this.engine = engine;
			this.color  = color;
			}
		carStats(){
			return `This car has ${this.door} doors,
	        a ${this.engine} and ${this.color} color!`
			}
		}

		const car1 = new Car(4, 'v8', 'grey');
		console.log(Car.length);
		console.log(car1.color);
		console.log(car1.doors);
		console.log(car1.doors.toString());

### Constructors  
#### Introduction to Constructors  
Method to create object when a new instance of a class is created.  
Constructor are part of syntax of a class, if you don't create one will be automatically generated.  
Only one constructor per class.  
Constructor builds initial object for us.  

#### Constructor and super usage

	class Car{
		constructor(doors, engine, color){
			this.doors  = doors;
			this.engine = engine;
			this.color  = color;
			}

		carStats(){
			return `This car has ${this.door} doors,
	        a ${this.engine} and ${this.color} color!`
		}
	}

	class SUV extends Car {
		constructor(doors, engine, color, brand, carStats){
			super(doors, engine, color, carStats);
			this.brand = brand;
			this.wheels = 4;
			this.ac = true;
		}
		myBrand(){
				return console.log(`This SUV is a ${this.brand}`);
		}
	}

	const cx5 = new SUV(4, 'v8', 'grey', 'mazda');
	const civic = new Car(3, 'v5', 'red');
	console.log(cx5);
	console.log(civic);


### Extends and Mixins  
#### Extends Intro and Usage  
Leveraging another classe to create your own.
eg_ Extending stateful class in react

	import React, { Component } from 'react';
	
	class Button extends Component {
		render() {
			return ( <button> Hello </button> )
		}
	}

	export default Button;

Practice React application to get a strong hold of the concept.

#### Mixins Intro and Usage  
Mixins
Extend more than one class in a single class.
As per gang of four this is one pattern where favour composition over inheritance.

Multiple ways to add mixins to the class.
Caution Dont use in regular code as inceases complexity.

	let mixins = {
		madeIn() {
			console.log('This car was made in year 2019!');
		}
	}

	let carMixins = {
		_proto_: mixin,

		madeIn(){
			super.madeIn()
		}
	}


	class Car{
		constructor(doors, engine, color){
			this.doors  = doors;
			this.engine = engine;
			this.color  = color;
			}

		carStats(){
			return `This car has ${this.door} doors, 
	        a ${this.engine} and ${this.color} color!`
		}
	}

	class SUV extends Car {
		constructor(doors, engine, color, brand, carStats){
			super(doors, engine, color, carStats);
				this.brand = brand;
				this.wheels = 4;
				this.ac = true;
				// assign mixin
				Object.assign(this, carMixin);
		}
	myBrand(){
			return console.log(`This SUV is a ${this.brand}`);
		}
	}

	const cx5 = new SUV(4, 'v8', 'grey', 'mazda');
	const civic = new Car(3, 'v5', 'red');
	console.log(cx5);
	console.log(cx5.myBrand());
	console.log(cx5.madeIn());

### Conclusion  
React js would be a great framework to practice these concepts.
