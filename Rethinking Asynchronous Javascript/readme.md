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

Non-Parallelism =  Waiting in line at amusement park but with 30 seat rollercoster only one is riding at a time. 
Parallelism = Waited in line and 30 people loaded and experiencing ride at the same time. 

P - Express through thread. Cues of action. 
One core is doing one work at a time. 
Single browser will take 10/15 threads just for basic operations.  
As OS doesn't have infinite number of cores, OS have layer called sort of virtual threads taking care of scheduling across cores.  
Parallelism is about optimisation.  

Asynchronicity - Single thread, programming inside js runs on a single thread. Even rosers have access to multiple threads. Node can use thosand of threads in the background. 
Only one line of js runs in js engine.  

Web worker is an example to bridge that gap with way of spinning up an entirely separate thread. But it's a broser thing. 

js programmer normally don't have to worry about threaded programming like dealing with mutexes, semaphores and shared resource locking.  Only one function can run at any given time.  

----------------------
#### Concurrency
Two higher level tasks happening with the same time frame. 

==========================================
### Callback 
Callback is function that is to be executed after 	another function has finished executing. 
In js functions are objects, Due to this functions can take functions as arguments and can be returned by other functions. Functions doing this are higher order function. Functions being passed as an argument is called a callback argument. 
 
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

----------------------
#### Callback problems: Inversion of Control 

----------------------
#### Callback problems: Not reasonable 

----------------------
#### Non fixes

==========================================
### Thunks 
----------------------
#### Synchronous and asynchronous thunks 

----------------------
#### Exercise 2 

----------------------
#### Exercise 2 solution

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
