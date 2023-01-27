## Challenge

- Implement the `min` function so that it returns the smallest value in numbers

## Solution

```javascript
const min = function (numbers) {
  return Math.min(...numbers);
};
```

## Explanation

- The function takes in an argument called `numbers`
- It uses the built-in `Math.min()` function and the spread operator (`...`) to find the smalled number in the `numbers` array.
- The spread operator is used to spread the elements of the `numbers` array as seperate arguments to the `Math.min()` function, which expects individual numbers as arguments.
- It then returns the smallest number in the `numbers` array.

## Test Cases

```javascript
const flightPrices = [1260, 490, 599, 1400, 820];
console.log(
  `The cheapest flight amongst $1260, $490, $599, $1400 and $820 costs \$${min(
    flightPrices
  )}`
);

// output: The cheapest flight amongst $1260, $490, $599, $1400 and $820 costs $490

const golfScores = [-1, 3, 0, -4, 1, 4, -2];
console.log(
  `The winning golf score amongst -1, 3, 0, -4, 1, 4 and -2 is ${min(
    golfScores
  )}`
);

// The winning golf score amongst -1, 3, 0, -4, 1, 4 and -2 is -4

const pageNumbers = [232];
console.log(
  `The shortest book out of a list of single book with 232 pages has ${min(
    pageNumbers
  )} pages`
);

// output: The shortest book out of a list of single book with 232 pages has 232 pages

const temperatures = [45, 10, -20, 0, 3, -20];
console.log(
  `The coldest temperature amongst 45C, 10C, -20C, 0C, 3C and -20C is ${min(
    temperatures
  )}C`
);

//output: The coldest temperature amongst 45C, 10C, -20C, 0C, 3C and -20C is -20C
```
