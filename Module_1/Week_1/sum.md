## Solution
```javascript
const add = function (numbers) {
  // iterate over the array and add them together
  return numbers.reduce((acc, num) => acc + num, 0);
};

// removes the first 2 elements of the array
const args = process.argv.slice(2);
// convert the array to numbers
const sum = args.map(Number);
console.log(add(sum));
```

## Explanation 

- We defined a function called `add` which takes in an array of numbers as its argument. 
- The function uses the `reduce` method to iterate over the array and add all the numbers together.
- The result is returned by the function.

- We then use the `slice` method to remove the first two elements of the `process.argv` array, which is an array that contains command line arguments passed to the node.js script.
- We then converted the array to numbers using the `map` method with the `Number function` as a callback.
- Finally, we call the add function passing the converted array and log the returned value.