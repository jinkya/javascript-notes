
## Arrays
Array a neat way to store continuous items in memory in a single variable. 
A global object that is used in the construction of arrays; which are high-level, list-like objects.   
**typeof array = object**  
**Declaration**  
let a = [];  
let b = new Array();   
**Length**   
array.length   
Setting an initial length with Array constructor 
let c = new Array(10) 

For best performance, use only one data type in one array.   
let projects = ["Telugu","Tamil","Marathi","Sanskrit","Hindi","Bengali"];   

**Access array elements**  
with index projects[0] = "Telugu"  

**Adding items to array**  
> **At the end (push)**   
> projects.push("spanish")   
> Changes the original array   

>**At the begin(unshift)**  
> projects.unshift("arabic")   
> Changes the original array   

>**At the begin (ES6 spread)**   
>projects = ["Sinhala",...projects]   
>Changes the original array   

>**At the end (ES6 spread)**  
> projects = [...projects, "Hindi"]   
> Changes the original array  

**Removing items from the array**  
>**At the begin ( shift )**  
> array.shift()  // removes the array first element  
> Modifies the original array  

 **At the end ( pop )**  
> array.pop()   // removes array last element  
> Modifies the original array  

 **Getting a copy (slice)**  
> array.slice(indexStart, numberOfElementsFromThatIndex)  
> Creates a new array  

**Deleting desire no of elements and adding ( splice )**  
> array.splice(start,deleteCount,replaceElement(s))  
> eg-  
> let projects = ["a",'b',"c","d","e","f","g"]  
var a = projects.splice(3,2,"w")  
console.log(a)          // ["d","e"]  
console.log(projects)   // ["a", "b", "c", "w", "f", "g"]  
let vara = ["ravi","som","budh"]  
var cha = vara.splice(2,0,"mangal")  
console.log(cha)    // []  
console.log(vara)   // ["ravi", "som", "mangal", "budh"]  

**Merging the Arrays**  
> **concat()**  
> Creates a new array  
> eg_  
> var a = [1,2]  
   var b = [3,4]  
   let merged = a.concat(b)  
   console.log(merged);    // [1,2,3,4]  

**es6 spread operator**   
>  var a = [5,6]  
     var b = [7,8]  
     var c = [...a, ...b]  
     console.log(c)          // [5, 6, 7, 8]  

**join()**  
> let vara = ["ravi","som","mangal"]  
vara.join()    //  "ravi,som,mangal"  
vara.join("-") // "ravi-som-mangal"  

**Loopin though Arrays**  
>**for**  

>**forEach**  
>array.forEach((e,index)=>{ console.log(index, e); })   

>**for of**  
>for( x of array ) { console.log(x) } // only numerable elements, not properties  

>**for in**  
>for(x in array) { console.log(x) } // numeral and non numeral indexes  

** Finding element in an array**  
>**find** only returns the first satisfying condition element  
>array.find((element, index, array)=> { console.log(element); return element.length > 5 })  

**Looping through Array**  
> **map()**  
> vara = ["ravi", "som", "mangal"]  
vara.map((el, index, array)=> { return el[1] })     // ["a", "o", "a"]  
.
vara = ["ravi", "som", "mangal"]  
vara.map((e, i)=> { return { key: i, value: e } } ) // [ {key:0, value: "ravi"},...]  

>**filter**  
>array.filter((e,i,arr)=>{ return condition })  


**The reduce() function**  
>var ao = [1,2,3,4]  
>console.log(ao.reduce((accumulator, current)=> { return accumulator+current })) // 10  
> [use cases](https://codeburst.io/all-about-javascript-arrays-in-1-article-39da12170b1c)  
> [technical details](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)  

**Creating emptiness with delete**  
> let ro = [1,2,3,4,5]  
delete ro[1]  
console.log(ro)  // [1, empty, 3, 4, 5]  

