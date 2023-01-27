## Solution

```javascript
const add = function (numbers) {
  // iterate over the array and add them together
  return numbers.reduce((acc, num) => {
    // checks if the items in the array are numbers and only adds them if they are
    if (!isNaN(num)) {
      return acc + num;
    }
    return acc;
  }, 0);
};

// removes the first 2 elements of the array
const args = process.argv.slice(2);
// convert the array to numbers
const sum = args.map(Number);
console.log(add(sum));
```

## Explanation

- We defined a function called `add` which takes in an array of numbers as its argument.
- The `reduce` method takes in 2 arguments, a callback function and an initial value. In this case, the callback function checks if the current element of the array, represented by the "`num`" variable, is a number by using the `isNaN()` function. If it is a number, it adds it to the accumulator, represented by the "`acc`" variable, and returns the new value of the accumulator. If the element is not a number, it simply returns the current value of the accumulator without making any changes. The initial value of the accumulator is set to `0`.
- The result is returned by the function.
- We then use the `slice` method to remove the first two elements of the `process.argv` array, which is an array that contains command line arguments passed to the node.js script.
- We then converted the array to numbers using the `map` method with the `Number function` as a callback.
- Finally, we call the add function passing the converted array and log the returned value.
