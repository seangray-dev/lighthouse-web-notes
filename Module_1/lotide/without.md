## Challenge

- Implement `without` which will return a subset of a given array, removing unwanted elements.

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

const without = function (source, itemsToRemove) {
  return source.filter((item) => {
    return !itemsToRemove.includes(item);
  });
};
```

## Explanation

- The `without` function takes in 2 parameters: `source` and `itemsToRemove`.
- THe function creates a new array from the `source` array by filtering out any items that are not in the `itemsToRemove` array.
- It uses the `filter` method to create a new array with all elements that pass the test of the function.
- The callback function takes `item` as an argument and checks whether the item is not included in the `itemsToRemove` array by using the the `includes` function and returns true if it is.
- The function returns a new array containing all elements of the `source` array that are not in the `itemsToRemove` array.

## Test Cases

```javascript
without([1, 2, 3], [1]); //output: [ 2, 3 ]
without(["a", "b", "c"], ["a"]); // output: ["b", "c"]
without(["1", "2", "3"], [1, 2, "3"]); // output: [ '1', '2' ]

const words = ["hello", "world", "lighthouse"];
without(words, ["lighthouse"]); // output: [ 'hello', 'world' ]
assertArraysEqual(words, ["hello", "world", "lighthouse"]); // output: true
```
