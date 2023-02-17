## Question 00

Write a converter that will change Celsius to Fahrenheit and back again.

Your function should take in a number, and a boolean. The number will be the temperature in degrees, and the boolean will be whether to convert from C to F (true) or F to C (false). Your answer should be rounded to one decimal place, and returned as a Number, not a string.

If the first argument is not a number, return NaN for the result.

## Answer 00

```javascript
const tempConverter = function (value, cToF) {
  if (typeof value !== "number" || typeof cToF !== "boolean") {
    return NaN;
  }

  if (cToF) {
    return parseFloat((value * 1.8 + 32).toFixed(1));
  }

  if (!cToF) {
    return parseFloat(((value - 32) / 1.8).toFixed(1));
  }
};
```

## Explanation

- This function takes in 2 arguments `value` and `cToF`.
- We first check if bothe the `value` and `cToF` are valid inputs. If `value` is not a number or if `cToF` is not a boolean we retrun `NaN`
- If both inputs are valid, we perform the conversion based off of the value of `cToF`.
  - if `cToF` is true, we convert the `value` from Celsisus to Farenheit using the formula `(value * 1.8 + 32`) we then use `toFixed(1)` to round down to one decimal place, and use `parseFloat()` to return a floating point number.
  - if `cToF` is false, we convert `value` from Farenheit to Celsius using the formula (`(value - 32) / 1.8`), again using `toFixed(1)` to round down to one decimal place, and `parseFloat()` to return a floating point number.

## Question 01

Build a function called `keyMatcher()` which, when passed two objects and a string, will use the string to look up the key-value pair in each object and compare the values. If the two values are explicitly equal to each other, return true, otherwise return false if either the values or not the same, or both objects do not have that key.

## Solution 01

```javascript
const keyMatcher = function (firstObj, secondObj, key) {
  if (typeof firstObj !== "object" || typeof secondObj !== "object") {
    return false;
  }

  if (!(key in firstObj) || !(key in secondObj)) {
    return false;
  }

  if (typeof firstObj[key] !== typeof secondObj[key]) {
    return false;
  }

  if (firstObj[key] !== secondObj[key]) {
    return false;
  }

  return true;
};
```

## Explanation

- `keyMatcher` takes in 3 arguments: `firstObj`, `secondObj` and `key`.
- First we check if the two objects `firstObj` and `secondObj` are indeed objects, and if they aren't we return `false` immediately.
- The second `if` statement is used to check if either objects have the `key` in them. If not we return `false`. We can use the `in` operator to check if an object has a particular property.
- The third `if` statement is used to check if the type of value `key` are the same type in both objects, if they aren't we return `false`.
- The last `if` statement is used to check if the values of `key` in `firstObject` and `secondObject` are the same values, if they aren't we return `false`.
- If all checks pass we return `true`.

## Question 02

Implement a function called `countWhich()` which will take in a list of items and a callback, and it will return the number of elements which return a truthy value from the callback function.

## Solution 02

```javascript
const countWhich = function (list, cb) {
  if (!Array.isArray(list)) {
    return false;
  }

  let count = 0;
  for (let i = 0; i < list.length; i++) {
    if (cb(list[i])) {
      count += 1;
    }
  }

  return count;
};
```

## Explanation

- `countWhich` takes in 2 arguments: `list` being an array and `cb` being a callback function.
- The first `if` statement checks is `list` is an array, if it isnt, we return `false`
- We decalre a variable `count` initialized to `0` to keep track of the number of elements in the array return a truthy value from the callback function.
- We use a `for` loop iterating over the elements of the `list`, and pass each element of the array to the `cb` function, if the `cb` returns true, the `count` is incremented by 1.
- After the loop has completed, we return the `count` variable.

## Question 03

Build out the function range() so that it takes three parameters:

1. The number of integers to generate
2. A boolean for whether to skip 0 or not (true: skip zero)
3. A boolean for whether the range should be in reverse/decreasing order or regular/increasing order (true: reverse/decreasing order)

If a non-number is passed in for the first argument, return an empty array.

## Solution 03

```javascript
const range = function (count, skipZero, descending) {
  let result = [];

  if (typeof count !== "number") {
    return result;
  }

  if (!skipZero && !descending) {
    for (let i = 0; i < count; i++) {
      result.push(i);
    }
  } else if (!skipZero && descending) {
    for (let i = count - 1; i >= 0; i--) {
      result.push(i);
    }
  } else if (skipZero && !descending) {
    for (let i = 1; i <= count; i++) {
      result.push(i);
    }
  } else {
    for (let i = count; i > 0; i--) {
      result.push(i);
    }
  }

  return result;
};
```

## Explanation

- `range` takes in 3 arguments: `count`, `skipZero`, & `descending`.
- We initilaize an empty array `result`
- The first `if` statement checks if `count` is not a number, if it isnt we return the empty array `result`.
- If `skipZero` is false and `descending` is false, we generate a new array from 0, to `count - 1` using a `for` loop and `push` each number to `result`
- If `skipZero` is false and `descending` is true, we generate a new array from `count - 1` to 0 using a `for` loop and `push` each nuymber to `result`.
- If `skipZero` is true and `descending` is false, we generate a new array from 1 to `count` using a `for` loop and `push` each number to `result`
- If both `skipZero` and `descending` are true, we genereate a new array from `count` to 1, using a `for` loop and `push` eahc number to `result`.
- Last we return the `result`.

## Question 04

Given an array of values, the `minmax()` function will return an array that contains the minimum and maximum values in the array, always with minimum at index 0 and maximum at index 1. For the purposes of this question, you are not allowed to use `Math.max()` or `Math.min()`.

## Solution 04

```javascript
const minmax = function (list) {
  if (list.length === 0) {
    return [undefined, undefined];
  }

  let min = list[0];
  let max = list[0];

  for (let i = 1; i < list.length; i++) {
    if (list[i] > max) {
      max = list[i];
    } else if (list[i] < min) {
      min = list[i];
    }
  }

  return [min, max];
};
```

## Explanation

- `minmax` takes in an array `list`
- The first `if` statement checks if the lenght of the `list` is 0, if it is we return an array containing two `undefined` values.
- We declare 2 variables `min` and `max` both intialized to `list[0]`
- The `for` loop iterates over the remaining elements in the array `list` using an index `i = 1`
- For each element in the array, we check if the element is greater than the value of `max` if it is we update our `max` value: `max = list[i]`
- If the elemeent is not greater than `max` we check if the element is less than our current value of `min` and if it is we update our `min` value: `min = list[i]`
- After the loop has finished we return an array contianing our the values of `min` and `max`: `return [min, max]`
