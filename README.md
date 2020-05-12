# JavaScript-snippets
<img src="Logo.png" alt="JS snippets logo">

# JSsnippets on Facebook

find us on [Facebook](https://www.facebook.com/snippetsJS)


# How to generate a random number in a given range

```javascript
// Returns a random number(float) between min (inclusive) and max (exclusive) 

const getRandomNumber = (min, max) => Math.random() * (max - min) + min;

getRandomNumber(2, 10)

 // Returns a random number(int) between min (inclusive) and max (inclusive)

const getRandomNumberInclusive =(min, max)=> {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

getRandomNumberInclusive(2, 10);
```

# How to find the difference between two arrays.


```javascript
const firstArr = [5, 2, 1];
const secondArr = [1, 2, 3, 4, 5];

const diff = [
    ...secondArr.filter(x => !firstArr.includes(x)),					
    ...firstArr.filter(x => !secondArr.includes(x))
];
console.log('diff',diff) //[3,4]


function arrayDiff(a, b) {
    return [
        ...a.filter(x => b.indexOf(x) === -1),
        ...b.filter(x => a.indexOf(x) === -1)
    ]
}
console.log('arrayDiff',arrayDiff(firstArr, secondArr)) //[3,4]




const difference = (a, b) => {
    const setA = new Set(a);
    const setB = new Set(b);

    return [
        ...a.filter(x => !setB.has(x)),
        ...b.filter(x => !setA.has(x))

    ]
};

difference(firstArr, secondArr); //[3,4]
console.log('difference',difference(firstArr, secondArr))
```

# How to convert truthy/falsy to boolean(true/false)
```javascript
const myVar = null; 
const mySecondVar = 1; 

console.log( Boolean(myVar) ) // false
console.log( !!myVar ) // false


console.log( Boolean(mySecondVar) ) // true
console.log( !!mySecondVar ) // true
```

# How to repeat a string
```javascript

let aliens = '';

for(let i = 0 ; i < 6 ; i++){
 aliens += '👽'
}
//👽👽👽👽👽👽

Array(6).join('👽')
//👽👽👽👽👽👽


'👽'.repeat(6)
//👽👽👽👽👽👽

```
# Check how long an operation takes
```javascript
//The performance.now() method returns a DOMHighResTimeStamp, measured in milliseconds.
//performance.now() is relative to page load and more precise in orders of magnitude. 
//Use cases include benchmarking and other cases where a high-resolution time is required 
//such as media (gaming, audio, video, //etc.)

var startTime = performance.now();
doSomething();
const endTime = performance.now();
console.log("this doSomething took " + (endTime - startTime) + " milliseconds.");
```

# Two ways to remove an item in a specific in an array

```javascript
//Mutating way
const muatatedArray = ['a','b','c','d','e'];
muatatedArray.splice(2,1)
console.log(muatatedArray) //['a','b','d','e']

//Non-mutating way
const nonMuatatedArray = ['a','b','c','d','e'];
const newArray = nonMuatatedArray.filter((item, index) => !( index === 2 ));
console.log(newArray) //['a','b','d','e']
```

# Did you know you can flat an array?

```javascript
const myArray = [2, 3, [4, 5],[7,7, [8, 9, [1, 1]]]];

myArray.flat() // [2, 3, 4, 5 ,7,7, [8, 9, [1, 1]]]

myArray.flat(1) // [2, 3, 4, 5 ,7,7, [8, 9, [1, 1]]]

myArray.flat(2) // [2, 3, 4, 5 ,7,7, 8, 9, [1, 1]]

//if you dont know the depth of the array you can use infinity
myArray.flat(infinity) // [2, 3, 4, 5 ,7,7, 8, 9, 1, 1];

```

# Get unique values in an array

```javascript
const numbers = [1,1,3,2,5,3,4,7,7,7,8];

//Ex1
const unieqNumbers = numbers.filter((v,i,a) => a.indexOf(v )=== i )
console.log(unieqNumbers) //[1,3,2,5,4,7,8]

//Ex2
const unieqNumbers2 = Array.from(new Set(numbers))
console.log(unieqNumbers2) //[1,3,2,5,4,7,8]

//Ex3
const unieqNumbers3 = [...new Set(numbers)]
console.log(unieqNumbers3) //[1,3,2,5,4,7,8]

//EX4 lodash
const unieqNumbers4 = _.uniq(numbers)
console.log(unieqNumbers4) //[1,3,2,5,4,7,8]

```
# Copy Text to Clipboard


```javascript
function copyToClipboard() {

  const copyText = document.getElementById("myInput");
  copyText.select();
  document.execCommand("copy");
  
}
//new API
function copyToClipboard(){
 navigator.clipboard.writeText(document.querySelector('#myInput').value)
}

```

#  Nested Destructuring


```javascript
const user = {
 id: 459,
 name: 'JS snippets',
 age:29,
 education:{
  degree: 'Masters'
 }
}

const { education : { degree } } = user;
console.log(degree) //Masters
```

#  URLSearchParams 


```javascript
//The URLSearchParams interface defines utility methods to work with the query string of a URL.

const urlParams = new URLSearchParams("?post=1234&action=edit");

console.log(urlParams.has('post')); // true
console.log(urlParams.get('action')); // "edit"
console.log(urlParams.getAll('action')); // ["edit"]
console.log(urlParams.toString()); // "?post=1234&action=edit"
console.log(urlParams.append('active', '1')); // "?post=1234&action=edit&active=1"
```


#  Shuffle an array 


```javascript
const list = [1,2,3,4,5,6,7,8,9];
const shuffle = list.sort(func);

function func(a,b){
  return 0.5 - Math.random();
}

console.log(shuffle);
```

#  Count elements in an array


```javascript
const myFruits = ['Apple','Orange','Mango','Banana','Apple','Apple','Mango']

//first option
const countMyFruits = myFruits.reduce((countFruits,fruit) => {
  countFruits[fruit] = ( countFruits[fruit] || 0 ) +1;
  return countFruits
 },{} )
 console.log(countMyFruits)
 // { Apple:3, Banana:1, Mango:2, Orange:1 }
 
 //seconf option
 const fruitsCounter = {};
 
 for( const fruit of myFruits ){
   fruitsCounter[fruit] = fruitsCounter[fruit] ? fruitsCounter[fruit]+1 :1;
 }
  
 console.log(fruitsCounter)
 // { Apple:3, Banana:1, Mango:2, Orange:1 }
```


#  Aliases with JavaScript Destructuring


```javascript

//There are cases where you want the destructured variable to have a different name than the property name

const obj = { 
  name: "JSsnippets"													
};


// Grabs obj.name as { pageName }
const { name: pageName } = obj;

//log our alias
console.log(pageName) // JSsnippets
```



#  The Object.is() method determines whether two values are the same value


```javascript
Object.is('foo', 'foo');     // true

Object.is(null, null);       // true

Object.is(Nan, Nan);       // true 😱

const foo = { a: 1 };
const bar = { a: 1 };
Object.is(foo, foo);         // true
Object.is(foo, bar);         // false

```



#  How can we freeze an object


```javascript
const obj = { 
  name: "JSsnippets",
  age:29,
  address:{
	  street : 'JS'
	}
};														

const frozenObject = Object.freeze(obj);

frozenObject.name = 'weLoveJS'; // Uncaught TypeError

//Although, we still can change a property’s value if it’s an object:

frozenObject.address.street = 'React'; // no error, new value is set


delete frozenObject.name // Cannot delete property 'name' of #<Object>


//We can check if an object is frozen by using
Object.isFrozen(obj) //true

```


#  Printing Object keys and values


```javascript
const obj = { 
  name: "JSsnippets",
  age:29,
};

//Object.entries() method is used to return an array consisting of enumerable property 
//[key, value] pairs of the object which are passed as the parameter.

for(let [key,value] of Object.entries(obj)){
   console.log(`${key}: ${value}`)
}

//expected output:
// "name: Jssnippets"
// "age: 29"
// order is not guaranteed

```
#  Capture the right click event

```javascript
window.oncontextmenu = () => {
	console.log('right click');
	return false // cancel default menu
}
//or

window.addEventListener('contextmenu', ()=>{
	console.log('right click');
	return false // cancel default menu
},false)
```


#  In HTML5, you can tell the browser when to run your JavaScript code
```javascript

//Without async or defer, browser will run your script immediately, before rendering the elements that's below your script tag.
<script src="myscript.js"></script>

//With async (asynchronous), browser will continue to load the HTML page and render it while the browser load and execute the script at the same time.
//Async is more useful when you really don't care when the script loads and nothing else that is user dependent depends upon that script loading.(for scripts likes Google analytics)
<script async src="myscript.js"></script>

//With defer, browser will run your script when the page finished parsing. (not necessary finishing downloading all image files. 
<script defer src="myscript.js"></script>
```

#   nullish coalescing operator
```javascript

// an equality check against nullary values (e.g. null or undefined). Whenever the expression to the left of the ?? operator evaluates to either //undefined or null, the value defined to the right will be returned.

const foo = undefined ?? 'default string';
console.log(foo);
// expected output: "default string"


const age = 0 ?? 30;
console.log(age);
// expected output: "0"
```

#  Optional chaining
```javascript

const car = {}
const carColor = car.name.color
console.log(carColor);
// error- "Uncaught TypeError: Cannot read property 'carColor' of undefined		

//In JavaScript, you can first check if an object exists, and then try to get one of its properties, like this:
const carColor = car && car.name && car.name.color;
console.log(carColor);
//undefined- no error


//Now this new optional chaining operator will let us be even more fancy:

const newCarColor = car?.name?.color;
console.log(newCarColor) 
//undefined- no error
					
//You can use this syntax today using @babel/plugin-proposal-optional-chaining
```

#  globalThis
```javascript
Accessing the global property in JavaScript has always posed some difficulty. This is because 
different platforms have different ways to access it.

Client-side JavaScript uses window or self

Node.js uses global

Web workers use self

The globalThis property provides a standard way of accessing the global 'this' value across environments. you can access the global object in a consistent manner without having to know which environment the code is being run in. 

console.log(globalThis) //get the global this depends on your environment

```



#  The second argument of JSON.stringify lets you cherry-pick 🍒 keys to serialize.
```javascript
const user = {
 id: 459,
 name: 'JS snippets',
 age:29,
 education:{
  degree: 'Masters'
 }
}

JSON.stringify(user,[name,age], 2)						

/*
returns

{
  "name": "JS snippets",
  "age": 29
}


*/

```


#  Fire an event listener only once.
```javascript
const el = document.getElementById("btn");

function myClickHandler(){
  console.log('this click will only fire once')
}


el.addEventListener('click', myClickHandler, {
  once: true,
});

```

#  Vanilla JS toggle
```javascript
const span = document.querySelector("span");
let classes = span.classList;

span.addEventListener("click", function() {
  let result = classes.toggle("active");

  if (result) {
    console.log("active class was added");
  } else {
    console.log("active class was removed");
  }
});

```
# Check if a string is a valid JSON

```javascript
function isJson(str) {
    try {
        JSON.parse(str);
    } catch (e) {
      //the json is  not ok
        return false;
    }
    //the json is ok
    return true;									
}
```

# getBoundingClientRect

```javascript
//getBoundingClientRect provides you with important pieces of data about an
//HTML element’s size and positioning.

const bodyBounderies = document.body.getBoundingClientRect();
// =>  {
//       top: Number,
//       left: Number,
//       right: Number,
//       bottom: Number,
//       x: Number,
//       y: Number,
//       width: Number,
//       height: Number,
//     }
```


# Check if a node is in the viewport
bonus: add/remove animation depending if an image is in the viewport
https://codepen.io/JSsnippets/pen/PoqrjEY
```javascript
const image = document.querySelector('.animate-me');

observer = new IntersectionObserver((entries) => {
  const [ myImg ] = entries;
    if (myImg.intersectionRatio > 0) {
      myImg.target.classList.add('fancy');
    } else {
      myImg.target.classList.remove('fancy');
    }
});


observer.observe(image);

```


