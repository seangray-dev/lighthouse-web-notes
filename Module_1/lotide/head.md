## Challenge

- Create a function `head` which returns the first item in the array.
- Use `assertEqual` to write test cases for various scenarios.
- Think of other scenarios to consider
  - An array with only one element should still yield that one element as it's head.
  - Am empty array should yield `undefined` as it's head.

## Solution

```javascript
const assertEqual = function (actual, expected) {
  if (actual === expected) {
    return `✅ Assertion Passed: [${actual}] === [${expected}]`;
  } else {
    return `🛑 Assertion Failed: [${actual}] !== [${expected}]`;
  }
};

const head = function (array) {
  if (array.length) {
    return array[0];
  } else {
    return undefined;
  }
};
```

## Explanation

- The function named `head` takes in an argument of `array`
- It checks if the length of the array is greater than 0.
- If the length of the array is greater than 0, the function returns the first element in the array `array[0]`
- Otherwise, it returns the value `undefined`
- We can use this function to retreive the first element in an array.

## Test Cases

Using the assertEqual helper function to test:

```javascript
assertEqual(head([5, 6, 7]), 5);
// output: ✅ Assertion Passed: [5] === [5]

assertEqual(head(["Hello", "Lighthouse", "Labs"]), "Hello");
// output: ✅ Assertion Passed: [Hello] === [Hello]

assertEqual(head([]), "Hello");
// output: 🛑 Assertion Failed: [undefined] !== [Hello]
```
