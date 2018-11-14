## Javascript Classes

    Lynda
    Emmanuel Henri
    37 m 18 s

---
#### Introduction  
Classes  
ES6 for better prorotype syntax.  
Syntactic sugar over prototypes.  
Classes changes get passed dropdowns.  
Classes aren't hoisted at top thus required to declare first to use it.  
Two ways to define - Class Declaration and Class Expression.  
Properties and Methods can be attached to methods.  
  
#### Defining classes  
emmet plugin for the synatctic shortcut.  
Install Live Server Plugin ( Start a server with simple command - Shift Ctr P - Live Server Open - Browser).  

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

Difference between Functions and Classes  
|Functions| Classes |
|--|--|
| Hoisted | Not Hoisted |
| Can be overwritten | Can't be overwritten( can be extended) |

When create a blueprint resuse and still need functions create a class  
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

Hoisting  
Try to use the use of classes above the Class Declaration, you will get a reference error.  
Thus always declare the class before using it.  
Function have different hoisting ways.  
  
strict mode (ES 5 )  
[Explore](https://mzl.la/1onrGsw)  
Make developer more aware about hoisting and other best practices adding some eror as throw away e.  
Also improves performance with review for better compilation.  
When declare a class it's automatically in strict mode.  
Also all its properties and methods.  
  
Static method and usage  
Aren't accesible through instance of class but only through class itself.  
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

	const cx5 = new Car(4, 'v7', 'white');
	const cx6 = new Car(2, 'v5', 'blue');
	console.log(cx5);
	console.log(cx5.carStats());
	console.log(Car.totalDoors(cx5, cx6));

Prototype Methods exlpained  
Class is just syntactical sugar over prototype   
Inherits the methods of prototype.  
console.log(cx5);  
_proto_ { constructo, carStats(many prperties binded) }  

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
		console.log(Car.length);
		console.log(cx5.color);
		console.log(cx5.doors);
		console.log(cx5.doors.toString());

Introduction to Constructors  
Method to create object when a new instance of a class is created.  
Constructor are part of syntax of a class, if you don't create one will be automatically generated.  
Only one constructor per class.  
Constructor builds initial object for us.  
  
Super Keyword 
Allows to access the methods of the parent class.  
  



#### Constructors  

#### Extends and Mixins  

#### Conclusion  
