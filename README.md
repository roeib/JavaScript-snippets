# JavaScript-snippets
> Click :star:  if you like the project. Pull Request are highly appreciated. Follow us on [Facebook](https://www.facebook.com/snippetsJS)

### Table of Contents
| No. | Questions |
|---- | ---------
|1  | [Generate a random number in a given range](#How-to-generate-a-random-number-in-a-given-range) |
|2  | [Find the difference between two arrays](#How-to-find-the-difference-between-two-arrays)|
|3  | [Convert truthy/falsy to boolean(true/false)](#Convert-truthy-falsy-to-boolean)|
|4  | [Repeat a string](#Repeat-a-string)|
|5  | [Check how long an operation takes](#Check-how-long-an-operation-takes)|
|6  | [Two ways to remove an item in a specific in an array](#Two-ways-to-remove-an-item-in-a-specific-in-an-array)|
|7  | [Did you know you can flat an array?](#Did-you-know-you-can-flat-an-array)|
|8  | [Get unique values in an array](#Get-unique-values-in-an-array)|
|9  | [Copy Text to Clipboard](#Copy-Text-to-Clipboard)|
|10 | [Nested Destructuring](#Nested-Destructuring)|
|11 | [URLSearchParams](#URLSearchParams)|
|12 | [Count elements in an array](#Count-elements-in-an-array)|
|13 | [Aliases with JavaScript Destructuring](#Aliases-with-JavaScript-Destructuring)|
|14 | [The Object.is() method determines whether two values are the same value](#the-objectis-method-determines-whether-two-values-are-the-same-value)|
|15 | [Freeze an object](#Freeze-an-object)|
|16 | [Printing Object keys and values](#Printing-Object-keys-and-values)|
|17 | [Capture the right click event](#Capture-the-right-click-event)|
|18 | [In HTML5, you can tell the browser when to run your JavaScript code](#in-html5-you-can-tell-the-browser-when-to-run-your-javascript-code)|
|19 | [Nullish coalescing operator](#Nullish-coalescing-operator)|
|20 | [Optional chaining](#Optional-chaining)|
|21 | [globalThis](#globalThis)|
|22 | [The second argument of JSON.stringify lets you cherry-pick 🍒 keys to serialize.](#the-second-argument-of-jsonstringify-lets-you-cherry-pick--keys-to-serialize)|
|23 | [Fire an event listener only once.](#Fire-an-event-listener-only-once)|
|24 | [Vanilla JS toggle](#Vanilla-JS-toggle)|
|25 | [Check if a string is a valid JSON](#Check-if-a-string-is-a-valid-JSON)|
|26 | [getBoundingClientRect](#getBoundingClientRect)|
|27 | [Check if a node is in the viewport](#Check-if-a-node-is-in-the-viewport)|
|28 | [Notify when element size is changed](#Notify-when-element-size-is-changed)|
|29 | [Detect if Browser Tab is in the view](#Detect-if-Browser-Tab-is-in-the-view)|
|30 | [Private class methods and fields](#Private-class-methods-and-fields)|
|31 | [Preventing paste into an input field](#Preventing-paste-into-an-input-field)|
|32 | [The void operator](#The-void-operator)|
|33 | [replaceAll](#replaceAll)|
|34 | [Required Function Params](#Required-Function-Params)|
|35 | [Get input value as a number](#Get-input-value-as-a-number)|
|36 | [reduceRight](#reduceRight)|
|37 | [Abort Fetch](#Abort-Fetch)|
|38 | [How to change the value of an object which is inside an array](#How-to-change-the-value-of-an-object-which-is-inside-an-array)|
|39 | [Numeric separators allow us to improve our code readability](#Numeric-separators-allow-us-to-improve-our-code-readability)|
|40 | [pay attention when using every](#pay-attention-when-using-every)|
|41 | [How to convert an array of key-value tuples into an object](#How-to-convert-an-array-of-key-value-tuples-into-an-object)|
|42 | [Native text to speech JS](#Native-text-to-speech-JS)|
|42 | [toFixed](#toFixed)|





**[⬆ Back to Top](#table-of-contents)**
### How to generate a random number in a given range
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

**[⬆ Back to Top](#table-of-contents)**
### How to find the difference between two arrays

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

**[⬆ Back to Top](#table-of-contents)**
### Convert truthy falsy to boolean

```javascript
const myVar = null; 
const mySecondVar = 1; 

console.log( Boolean(myVar) ) // false
console.log( !!myVar ) // false


console.log( Boolean(mySecondVar) ) // true
console.log( !!mySecondVar ) // true
```
**[⬆ Back to Top](#table-of-contents)**
### Repeat a string
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
**[⬆ Back to Top](#table-of-contents)**
### Check how long an operation takes
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

**[⬆ Back to Top](#table-of-contents)**
### Two ways to remove an item in a specific in an array

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

**[⬆ Back to Top](#table-of-contents)**
### Did you know you can flat an array

```javascript
const myArray = [2, 3, [4, 5],[7,7, [8, 9, [1, 1]]]];

myArray.flat() // [2, 3, 4, 5 ,7,7, [8, 9, [1, 1]]]

myArray.flat(1) // [2, 3, 4, 5 ,7,7, [8, 9, [1, 1]]]

myArray.flat(2) // [2, 3, 4, 5 ,7,7, 8, 9, [1, 1]]

//if you dont know the depth of the array you can use infinity
myArray.flat(infinity) // [2, 3, 4, 5 ,7,7, 8, 9, 1, 1];

```

**[⬆ Back to Top](#table-of-contents)**
### Get unique values in an array

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

**[⬆ Back to Top](#table-of-contents)**
### Copy Text to Clipboard


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

**[⬆ Back to Top](#table-of-contents)**
###  Nested Destructuring


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

**[⬆ Back to Top](#table-of-contents)**
###  URLSearchParams 


```javascript
//The URLSearchParams interface defines utility methods to work with the query string of a URL.

const urlParams = new URLSearchParams("?post=1234&action=edit");

console.log(urlParams.has('post')); // true
console.log(urlParams.get('action')); // "edit"
console.log(urlParams.getAll('action')); // ["edit"]
console.log(urlParams.toString()); // "?post=1234&action=edit"
console.log(urlParams.append('active', '1')); // "?post=1234&action=edit&active=1"
```

**[⬆ Back to Top](#table-of-contents)**
###  Count elements in an array


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

**[⬆ Back to Top](#table-of-contents)**
###  Aliases with JavaScript Destructuring


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


**[⬆ Back to Top](#table-of-contents)**
###  The Object.is() method determines whether two values are the same value


```javascript
Object.is('foo', 'foo');     // true

Object.is(null, null);       // true

Object.is(Nan, Nan);       // true 😱

const foo = { a: 1 };
const bar = { a: 1 };
Object.is(foo, foo);         // true
Object.is(foo, bar);         // false

```


**[⬆ Back to Top](#table-of-contents)**
###  Freeze an object


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

**[⬆ Back to Top](#table-of-contents)**
###  Printing Object keys and values


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

**[⬆ Back to Top](#table-of-contents)**
###  Capture the right click event

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

**[⬆ Back to Top](#table-of-contents)**
###  In HTML5, you can tell the browser when to run your JavaScript code
```javascript

//Without async or defer, browser will run your script immediately, before rendering the elements that's below your script tag.
<script src="myscript.js"></script>

//With async (asynchronous), browser will continue to load the HTML page and render it while the browser load and execute the script at the same time.
//Async is more useful when you really don't care when the script loads and nothing else that is user dependent depends upon that script loading.(for scripts likes Google analytics)
<script async src="myscript.js"></script>

//With defer, browser will run your script when the page finished parsing. (not necessary finishing downloading all image files. 
<script defer src="myscript.js"></script>
```

**[⬆ Back to Top](#table-of-contents)**
###   Nullish coalescing operator
```javascript

// an equality check against nullary values (e.g. null or undefined). Whenever the expression to the left of the ?? operator evaluates to either //undefined or null, the value defined to the right will be returned.

const foo = undefined ?? 'default string';
console.log(foo);
// expected output: "default string"


const age = 0 ?? 30;
console.log(age);
// expected output: "0"
```

**[⬆ Back to Top](#table-of-contents)**
###  Optional chaining
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

**[⬆ Back to Top](#table-of-contents)**
###  globalThis
```javascript
Accessing the global property in JavaScript has always posed some difficulty. This is because 
different platforms have different ways to access it.

Client-side JavaScript uses window or self

Node.js uses global

Web workers use self

The globalThis property provides a standard way of accessing the global 'this' value across environments. you can access the global object in a consistent manner without having to know which environment the code is being run in. 

console.log(globalThis) //get the global this depends on your environment

```


**[⬆ Back to Top](#table-of-contents)**
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

**[⬆ Back to Top](#table-of-contents)**
###  Fire an event listener only once
```javascript
const el = document.getElementById("btn");

function myClickHandler(){
  console.log('this click will only fire once')
}


el.addEventListener('click', myClickHandler, {
  once: true,
});

```
**[⬆ Back to Top](#table-of-contents)**
###  Vanilla JS toggle
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

**[⬆ Back to Top](#table-of-contents)**
### Check if a string is a valid JSON

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
**[⬆ Back to Top](#table-of-contents)**
### getBoundingClientRect

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

**[⬆ Back to Top](#table-of-contents)**
### Check if a node is in the viewport
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

**[⬆ Back to Top](#table-of-contents)**
### Notify when element size is changed 
see our codepen: https://codepen.io/JSsnippets/pen/dyYoYVX
```javascript
const foo = document.getElementById("foo");

const observer = new ResizeObserver((entries) => {
  for (let entry of entries) {
    const cr = entry.contentRect;
    console.log = `Size: ${cr.width}px X ${cr.height}px`;
  }
});
observer.observe(foo);

```
**[⬆ Back to Top](#table-of-contents)**
### Detect if Browser Tab is in the view
play/pause video accordingly
see our codepen: https://codepen.io/JSsnippets/pen/gOapPzq
```javascript


const video =  document.getElementById("my-video");

const onVisibilitychange =()=>{
   return document.hidden 
     ? video.pause() 
     : video.play();
} 

document.addEventListener("visibilitychange", onVisibilitychange)

```


**[⬆ Back to Top](#table-of-contents)**
### Private class methods and fields
```javascript

class Students {
  #name;

  constructor(){
    this.#name = "JS snippets";
  }

  #privateMethod() {
    return 'Come and learn Js with us';
  }

  getPrivateMessage() {
      return this.#privateMethod();
  }
}

const instance = new Something();
console.log(instance.name); //=> undefined
console.log(instance.privateMethod); //=> undefined
console.log(instance.getPrivateMessage()); //=> Come and learn Js with us

```


**[⬆ Back to Top](#table-of-contents)**
### Preventing paste into an input field
see our codepen: https://codepen.io/JSsnippets/pen/qBbyMoJ

```javascript

const pasteBox = document.getElementById("paste-no-event");
pasteBox.onpaste = (e) => {
  e.preventDefault();
  return false;
};

```


**[⬆ Back to Top](#table-of-contents)**
### The void operator 
The void operator evaluates the given expression and then returns undefined.
```javascript


void 0;  		//returns undefined
void (0); 		//returns undefined
void {}; 		//returns undefined
void "JSsnippets; 	//returns undefined
void (0); 		//returns undefined
void (2 == '2'); 	//returns undefined
void anyfunction(); 	//returns undefined

```


**[⬆ Back to Top](#table-of-contents)**
### replaceAll 
the method string.replaceAll(search, replaceWith) replaces all appearances of search string with replaceWith.
```javascript


const str = 'this is a JSsnippets example';

const updatedStr = str.replace('example', 'snippet'); // 'this is a  JSsnippets snippet'


The tricky part is that replace method replaces only the very first match of the substring we have passed:


const str = 'this is a JSsnippets example and examples are great';

const updatedStr = str.replace('example', 'snippet'); //'this is a JSsnippets snippet and examples are great'

In order to go through this, we need to use a global regexp instead:


const str = 'this is a JSsnippets example and examples are great';

const updatedStr = str.replace(/example/g, 'snippet'); //'this is a JSsnippets snippet and snippets are greatr'

but now we have new friend in town, replaceAll

const str = 'this is a JSsnippets example and examples are great';

const updatedStr = str.replaceAll('example', 'snippet'); //'this is a JSsnippets snippet and snippets are greatr'

```


**[⬆ Back to Top](#table-of-contents)**
### Required Function Params 
Expanding on the default parameter technique, we can mark a parameter as mandatory

```javascript
const isRequired = () => {
    throw new Error( 'This is a mandatory parameter.' );
}


const getPage = ( pageName = 'Jssnippets', url = isRequired() ) => {
    return `${pageName} ${url}`;
}

console.log(getPage());

//In the above code, url will be undefined and that will try to set the default value for it which is the isRequired() function. It will throw an error as,

//Uncaught error: This is a mandatory parameter.
//at isRequired

```




**[⬆ Back to Top](#table-of-contents)**
### Get input value as a number

```javascript

<input type="number" id="JSsnippets" onkeyup="checkMyType(event)" />

function checkMyType(event){
  
  console.log(typeof event.target.value) // string
  console.log(typeof event.target.valueAsNumber ) // number

}


```
**[⬆ Back to Top](#table-of-contents)**
### reduceRight

```javascript

const arr = ["a", "b", "c", "d", "e"]

const reduceArray = arr.reduce((acc, current) => {
    return acc + current
}, "")
//return abcde

const reduceRightArray = arr.reduceRight((acc, current) => {
    return acc + current
}, "")
//return edcba

```


**[⬆ Back to Top](#table-of-contents)**
### Abort Fetch

```javascript


//HTML
<button id="download">Download</button>
<button id="abort">Abort</button>

//JS
let controller;

document.querySelector('#download').addEventListener('click', () => {
  controller = new AbortController();
  const signal = controller.signal;
  fetch('https://cdn.plyr.io/static/demo/View_From_A_Blue_Moon_Trailer-576p.mp4', {signal})
    .then(() => console.log('done'));
});

document.querySelector('#abort').addEventListener('click', function() {
  controller.abort();
});

```


**[⬆ Back to Top](#table-of-contents)**
### How to change the value of an object which is inside an array

```javascript

const state = [
  {
    userId: 1,
    name: "JSSnippets",
    isOwner: false,
  },
  {
    userId: 2,
    name: "React",
    isOwner: false,
  },
  {
    userId: 3,
    name: "Vue",
    isOwner: false,
  },
  {
    userId: 4,
    name: "Angular",
    isOwner: false,
  },
];

const newState = state.map((obj) =>
  obj.name === "JSSnippets" ? { ...obj, isOwner: true } : obj			
);

```

**[⬆ Back to Top](#table-of-contents)**
### Numeric separators allow us to improve our code readability

```javascript

100_000_000 === 100000000 // true

300_000 === 300000 //true

```





**[⬆ Back to Top](#table-of-contents)**
### pay attention when using every

Calling this method on an empty array will return true for any condition!


```javascript

const arr = []
const result = arr.every(x=> x==5)
console.log(result) //true

```





**[⬆ Back to Top](#table-of-contents)**
### How to convert an array of key-value tuples into an object


```javascript

const JSarr = [
    ['name', 'JSsnippets'],
    ['address', 'worldwide'],
    ['year', '2018'],
    ['followers', '15000']

];

const obj = Object.fromEntries(JSarr);
//{
//  "name": "JSsnippets",
// "address": "worldwide",
//  "year": "2018",
//  "followers": "15000"
//}
```

**[⬆ Back to Top](#table-of-contents)**
### Native text to speech JS


```javascript

const startSpeaking=()=>{

	let msg = document.getElementById("text-to-speech").value;
	let speech = new SpeechSynthesisUtterance();
	
	speech.lang = "en-US";
	speech.text = msg;
	speech.volume = 1;
	speech.rate = 1;
	speech.pitch = 1;

	window.speechSynthesis.speak(speech);
}


```

**[⬆ Back to Top](#table-of-contents)**
### toFixed

Warning: Floating point numbers cannot represent all decimals precisely in binary. This can lead to unexpected results, such as 0.1 + 0.2 === 0.3 returning false .

```javascript

123.678.toFixed()       // Returns '124'
123.678.toFixed(1)      // Returns '123.7': Note rounding

2.35.toFixed(1)        // Returns '2.4'. Note it rounds up
2.65.toFixed(1)        // Returns '2.6'. Note it rounds down -why??? see the warning above

```
