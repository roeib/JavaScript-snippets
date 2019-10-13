# JavaScript-snippets
JavaScript Snippets

```javascript
// Returns a random number between min (inclusive) and max (exclusive)

const getRandomNumber = (min, max) => Math.random() * (max - min) + min;

getRandomNumber(2, 10)

 // Returns a random number between min (inclusive) and max (inclusive)

const getRandomNumberInclusive =(min, max)=> {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

getRandomNumberInclusive(2, 10);
```
