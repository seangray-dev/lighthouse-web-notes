## Challenge

- Implement `assertArraysEqual` which will take in two arrays and console.log an appropriate message to the console.

## Solution

```javascript
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

const assertArraysEqual = function (array1, array2) {
  if (eqArrays(array1, array2)) {
    console.log("equal");
    return true;
  } else {
    console.log("not equal");
    return false;
  }
};
```

## Explanation

- The `assertArraysEqual` function takes in two parameters, `array1` and `array2`.
- It checkes if these 2 arrays are equal by calling the `eqArrays` function and passing in the two arrays as arguments.
- If the arrays are eqaul, the function will log `equal` to the console and return `true`.
- If the arrays are not eqaul, the function will log `not equal` to the console and return `false`.

## Test Cases

```javascript
assertArraysEqual([1, 2, 3], [1, 2, 3]); // returns true
assertArraysEqual([1, 2, "3"], [1, "2", 3]); // returns false
assertArraysEqual(["1", 2, 3], ["1", 2, 3]); // returns true
```
