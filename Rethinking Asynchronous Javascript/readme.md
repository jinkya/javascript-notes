
## Rethinking Asynchronous Javascript
    Kyle Simpson's Lynda Course
    6 h 22 m

--- 
### Parallel vs. Async 
----------------------
#### Introduction
Kyle Simpson
@getify


----------------------
#### Single threaded JavaScript 

Parallel vs Aysnc

Non-Parallelism =  Waiting in line at amusement park but with 30 seat rollercoster, only one is riding at a time. 
Parallelism = Waited in line and 30 people loaded and experiencing ride at the same time. 

Parallelism - Express through thread. Cues of action. 
One core is doing one work at a time. 
Single browser will take 10/15 threads just for basic operations.  
As OS doesn't have infinite number of cores, OS have layer called sort of virtual threads taking care of scheduling across cores.  
Parallelism is about optimization.  

Asynchronicity - Single thread, programming inside js runs on a single thread. Even browsers have access to multiple threads. Node can use thousand of threads in the background. 
Only one line of js runs in js engine.  

Web worker is an example to bridge that gap with way of spinning up an entirely separate thread. But it's a browser thing. 

js programmer normally don't have to worry about threaded programming like dealing with mutexes, semaphores and shared resource locking.  Only one function can run at any given time.  

----------------------
#### Concurrency
Two higher level tasks happening with the same time frame. 

==========================================
### Callback 
Callback is function that is to be executed after another function has finished executing. 
In JavaScript, functions are objects, Due to this functions can take functions as arguments and can be returned by other functions. Functions doing this are higher order function. Functions being passed as an argument is called a callback argument. 
 
 1.  Anything that is not a primitive type (undefined, null, number, string, boolean) is an object (or an instance) in JavaScript. That means  `function`  inherits from  `object`.
    
2.  Object instances can contain more instances which can be functions. That's what we call a "method" (since it has an automatic  `this`  variable).
    
3.  Since you can't "call" every Object instance, not every object is a function.
----------------------
#### Callback misery 
eg_
setTimeout(function(){
  console.log("callback!");
}, 1000);
cb === continuations

setTimeout(function(){
	console.log("1");
	setTimeout(function(){
		console.log("2");
		setTimeout(function(){
				console.log("3");
			},1000)
	},1000)
},1000)
.
Continuation Passing Style 

function one(cb){
	console.log("one");
	setTimeout(cb,1000);
}
function two(bc){
	console.log("two");
	setTimeout(cb,1000);
}
function two(bc){
	console.log("three");
}

one(function(){
	two(three);
})


----------------------
#### Exercise 1
Instructions 
1. This exercise calls for you to write some async flow-control code. To start off with, you'll use callbacks only.  
2. Expected behaviour:
- Request all 3 files at the same time ( in parallel )
- Render them ASAP ( don't just blindly wait for all to finish loading )
- BUT, render them in proper (obvious) order: "file1", "file2", "file3"
- After all 3 are done, output "Complete!".  


----------------------
#### Exercise 1: Solution 

	function fakeAjax(url,cb) {
		var fake_responses = {
			"file1": "The first text",
			"file2": "The middle text",
			"file3": "The last text"
		};
	var randomDelay = (Math.round(Math.random() * 1E4) % 8000) + 1000;
	console.log("Requesting: " + url);
	setTimeout(function(){
		cb(fake_responses[url]);
	},randomDelay);
	}
	
	function output(text) {
		console.log(text);
	}
	
	// **************************************
	// The old-n-busted callback way
	
	function getFile(file) {
		fakeAjax(file,function(text){
			fileReceived(file,text);
		});
	}

	function fileReceived(file,text) {
		// haven't received this text yet?
		if (!responses[file]) {
			responses[file] = text;
		}

	var files = ["file1","file2","file3"];
	
	// loop through responses in order for rendering
	for (var i=0; i<files.length; i++) {
		// response received?
		if (files[i] in responses) {
			// response needs to be rendered?
			if (responses[files[i]] !== true) {
				output(responses[files[i]]);
				responses[files[i]] = true;
			}
		}
		// can't render yet
		else {
			// not complete!
			return false;
		}
	}

	output("Complete!");
	}

	// hold responses in whatever order they come back
	var responses = {};

	// request all files at once in "parallel"
	getFile("file1");
	getFile("file2");
	getFile("file3");


----------------------
#### Callback problems: Inversion of Control 
Inversion of Control  
Code Execution Control Division

// line1
setTimeout(function(){
	// line 3
	// line 4
}, 1000)
// line 2

trackCheckout(
	purchaseInfo,
	function finish(){
		chargeCreditCard(purschaseInfo);
		showThankYouPage();
	}
);

  Trust ??
1. not too early 
2. not too late
3. not too many times 
4. not too few times 
5. no lost context 
6. no swallowed errors 

If you have a callback in any js program and no solution is provided for the every single trust issue, that program curently have a bug, even if not bitten by it. 

----------------------
#### Callback problems: Not reasonable 
Not Reasonable
Not abled to reason about. 
Maybe at highest level of cognition our brains are fundamentally single threaded. 
Sequential Synchronous step by step things are followed by the Brain 
That's how we code. 

	Sys Looking async 
		Synchronous 
		Sequential 
		Blocking 

----------------------
#### Non fixes
Non fixes 
Ways to fix the callback hell problem resulting in to more chaos. 
split callbacks 
The Meaning of Life Example Wikipedia

==========================================
### Thunks 
----------------------
#### Synchronous and asynchronous thunks 
Callback Patterns 
Thunk 
By a synchronous purpose, a thunk is a function that has everything already that it needs to do to give ou some value back, no need to provide arguments, just call it and it will give you a value back. 
Thunk is a function with some closured state keeping track of some value or values, and it givew the things back whenever you call the function 
eg_ 

function add(x, y){
	return x+y;
}
var thunk = function(){
	return add(10,15)
};
thunk();

A wrapper around a value. 

function addAsync(x,y,cb) {
	setTimeout(function(){
		cb(x+y);
	}, 1000)
}
var thunk = function(cb) {
	addAync(10, 15, cb)
}

thunk(function(sum){
	sum;
});

Managing Time is the most complex factor of state in your program! 

----------------------
#### Exercise 2 


----------------------
#### Exercise 2 solution
function fakeAjax(url,cb) {
	var fake_responses = {
		"file1": "The first text",
		"file2": "The middle text",
		"file3": "The last text"
	};
	var randomDelay = (Math.round(Math.random() * 1E4) % 8000) + 1000;

	console.log("Requesting: " + url);

	setTimeout(function(){
		cb(fake_responses[url]);
	},randomDelay);
}

function output(text) {
	console.log(text);
}

// **************************************

function getFile(file) {
	var resp;

	fakeAjax(file,function(text){
		if (!resp) resp = text;
		else resp(text);
	});

	return function th(cb) {
		if (resp) cb(resp);
		else resp = cb;
	};
}

// request all files at once in "parallel"
var th1 = getFile("file1");
var th2 = getFile("file2");
var th3 = getFile("file3");

th1(function ready(text){
	output(text);
	th2(function ready(text){
		output(text);
		th3(function ready(text){
			output(text);
			output("Complete!");
		});
	});
});

----------------------
#### Thunks and closure

==========================================
### Promises 
----------------------
#### Native promises 

----------------------
#### Promise api 

----------------------
#### Promise flow control 

----------------------
#### Exercise 3

----------------------
#### Exercise 3 solution 

----------------------
#### Exercise 3 questions, part 1

----------------------
#### Exercise 3 questions, part 2

----------------------
#### Exercise 4 

----------------------
#### Exercise 4 solution 

----------------------
#### Abstractions 

----------------------
#### Sequences and gates 

----------------------
#### Exercise 5 and 6 

----------------------
#### Exercise 5: Solution 

----------------------
#### Exercise 6: Solution 

==========================================
### Generators 
----------------------
#### Generator Example 

----------------------
#### Messaging 

----------------------
#### Messaging questions 

----------------------
#### Async generators 

----------------------
#### Promises and generrators 

----------------------
#### Exercise 7

----------------------
#### Exercise 7: Solution 

----------------------
#### Quiz

==========================================
### Observables 
----------------------
#### Events and promises

----------------------
#### Observables 

----------------------
#### Reactive sequences 

----------------------
#### Exercise 8 

----------------------
#### Exercise 8: Solution, part 1

----------------------
#### Exercise 8: Solution, part 2

==========================================
### CSP 
----------------------
#### Concurrency and channels 

----------------------
#### Blocking channels 

----------------------
#### Event channels 

----------------------
#### Exercise 9

----------------------
#### Exercise 9: Solution 

----------------------
#### Recap 

----------------------
#### Exercise 10

----------------------
#### Wrap-up 

==========================================
