## Challenge

- Implement a function eqArrays which takes in two arrays and returns true or false, based on a perfect match.
- Use `assertEqual` to write test cases for various scenarios.

## Solution

```javascript
const assertEqual = function (actual, expected) {
  if (actual === expected) {
    return `✅ Assertion Passed: [${actual}] === [${expected}]`;
  } else {
    return `🛑 Assertion Failed: [${actual}] !== [${expected}]`;
  }
};

const eqArrays = function (actual, expected) {
  if (actual.length !== expected.length) {
    return false;
  } else {
    for (let i = 0; i < actual.length; i++) {
      if (actual[i] !== expected[i]) {
        return false;
      }
    }
    return true;
  }
};
```

## Explanation

- The `eqArrays` function compares 2 arrays and returns `true` if they are equal, and `false` if they are not. It takes in 2 arguments: `actual` & `expected` which are the arrays to be compared.
- First the functions checks if the lengths of the 2 arrays are equal, and if they are not it immediately returns `false`.
- If they are equal, the `actual` array enters a for loop that iterates through each element of the array.
- For each iteration, it checks if the current element of the `actual` array is equal to the corresponding element of the `expected` array.
- If any of these comparisons are not equal, the function immediately returns `false`.
- If the loop completes without finding any mismatches, the function returns `true` letting us know that the 2 arrays are identical.

## Test Cases

```javascript
eqArrays([1, 2, 3], [1, 2, 3]);
// output: true

eqArrays(["1", "2", "3"], ["1", "2", 3]);
// output: false

assertEqual(eqArrays([1, 2, 3], [1, 2, 3]), true);
// output: ✅ Assertion Passed: [true] === [true]

assertEqual(eqArrays(["1", "2", "3"], ["1", "2", 3]), false);
// output: ✅ Assertion Passed: [false] === [false]
```
