## Challenge

- Implement the map function
- Write test cases using at least three different ways of using map.

## Solution

```javascript
const map = function (array, callback) {
  const results = [];
  for (let item of array) {
    results.push(callback(item));
  }
  return results;
};
```

## Explanation

- `map` takes an `array` and a `callback` function as arguments.
- We decalre a new variable called `results` with an empty array.
- We iterate through the `array` using a `for...of` loop and apply the `callback` function against it.
- If the result of the `callback` function returns `true`, it is pushed into the a new array `results`, if the callback returns `false` it doesn not.
- We then return the `results` array.

## Test Cases

```javascript
// Test 1
const people = ["sean", "melissa"];
const peopleResults = map(people, (item) => item.length); // -> [4, 7]
console.log(assertArraysEqual(peopleResults, [4, 7])); // -> true

// Test 2
const cookies = [
  { name: "🍪", type: "chocolate" },
  { name: "🍪", type: "oatmeal" },
  { name: "🥠", type: "fortune" },
  { name: "🍪", type: "peanut butter" },
];
const isChocCookie = map(cookies, (cookie) => cookie.type === "chocolate"); // -> [true, false, false, false]
console.log(assertArraysEqual(isChocCookie, [true, false, false, false])); // -> true

// Test 3
const numbers = [2, 4, 6, 8, 10];
const squareNum = (num) => num * num;
const squaredNumbers = map(numbers, squareNum); // -> [4, 16, 36, 64, 100]
console.log(assertArraysEqual(squaredNumbers, [4, 16, 36, 64, 100])); // -> true
```
