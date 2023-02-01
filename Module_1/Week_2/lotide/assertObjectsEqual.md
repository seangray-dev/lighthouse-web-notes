## Challenge

- Implement assertObjectsEqual which will take in two objects and console.log an appropriate message to the console.

## Solution

```javascript
const eqObjects = function (object1, object2) {
  // check if the number of keys in both objects are of the same length
  if (Object.keys(object1).length !== Object.keys(object2).length) {
    return false;
  }
  // loop through object1 keys
  for (const key in object1) {
    // check if both objects' keys are arrays
    if (Array.isArray(object1[key]) && Array.isArray(object2[key])) {
      // if they are, use eqArrays to compare the arrays
      if (!eqArrays(object1[key], object2[key])) {
        return false;
      }
    } else if (object1[key] !== object2[key]) {
      return false;
    }
  }

  return true;
};

const assertObjectsEqual = function (actual, expected) {
  const inspect = require("util").inspect;
  if (eqObjects(actual, expected)) {
    return `✅ Assertion Passed: ${inspect(actual)} === ${inspect(expected)}`;
  } else {
    return `🛑 Assertion Failed: ${inspect(actual)} !== ${inspect(expected)}`;
  }
};
```

## Explanation

- `assertObjectsEqual` takes in two objects as arguments: `actual` and `expected`.
- We use the `inspect` function from `util` module to display contents of the objects
- If `eqObjects(actual, expected)` returns `true` we return the message: `✅ Assertion Passed: ${inspect(actual)} === ${inspect(expected)}` saying that the objects are equal.
- Otherwise if `eqObjects(actual, expected)` returns `false` we return the message: `🛑 Assertion Failed: ${inspect(actual)} !== ${inspect(expected)}`

## Test Cases

```javascript
console.log(assertObjectsEqual({ a: "1", b: 2 }, { b: 2, a: "1" }));
// -> ✅ Assertion Passed: { a: '1', b: 2 } === { b: 2, a: '1' }
```
