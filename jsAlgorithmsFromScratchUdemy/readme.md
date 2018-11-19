
## Learning Algorithms in Javascript from scratch

	  Udemy Course by Eric traub
	  3.5 hours
  
### Introduction  
Efficient and Performing Algorithms
repl.it

### Fizz Buzz  
Console upto n numbers in a way that number divisible by 3 will be replaced with "Fizz", divisible by 5 with "Buzz" and divisible by both 3 and 5 with "FizzBuzz".  
Modulus Operator  
Returns the remainder 7 % 3 = 1  
[repl.it](https://repl.it/@AjinkyaNarwade/fizzBuzz)

### Algorithms and Big O notation  
[plain english explanation](https://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation)
[CLRS Book](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-introduction-to-algorithms-sma-5503-fall-2005/index.htm)
[cheatsheet](http://bigocheatsheet.com/)

Classify how scalable an algorithm or function is.  
Peformance with changing input data.  

O(1) Constant Runtime  
eg_ 

	function log(array){
		console.log(array[0]);
		console.log(array[1]);
	}
	log([1,2,3])

O(n) Linear Runtime   
Runtime is propotional to input.  
	
	function logAll(array){
		for(var i=0; i<array.length; i++){
			console.log(i);
		}
	}
	logAll([1,2,3])

O(n^2) Exponential Runtime  
eg_
	
	function addAndLog(array){
		for(var i=0; i<array.length; i++){
			for(var j=0; j<aray.length; j++){
				console.log(array[i]+aray[j]);
				}
		}
	} 
	andAndLog(['A','B','C']); // 9 pairs
	andAddLog(['A','B','C','D']) // 16 pairs

O(log n) Logarithmic runtime  
eg_ binary seach  

### Harmless Ransom Notes  
Is it possible to create a given string note from the existing string note.  
```
str.split([separator[, limit]])
```
Linear Time Complexity O(n)+O(m)  = O(n+m) = O(n)   
[repl.it](https://repl.it/@AjinkyaNarwade/harmlesRansomNote)  


### Is Palindrome  
Does it spell same as it in the reversed word.  
eg_   
race car.  
Madam, I'm Adam.
[repl.it](https://repl.it/@AjinkyaNarwade/isPalindrome)

### Caesar Cipher  
Shift every letter in the given string by the provided number.


### Reverse Words  

### Reverse Array in Place  

### Mean Median Mode  

### Two Sum  

### Binary Search  

### Fibonacci  

### Memoized Fibonacci  

### Sieve of Eratosthenes  

### bubble Sort  

### Merge Sort  

### Max Stock Profit    

### Next Steps  
