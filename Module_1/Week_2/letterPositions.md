## Challenge

- We'll implement a new function letterPositions which will return all the indices (zero-based positions) in the string where each character is found.

- For each letter, instead of returning just one number to represent its number of occurrences, multiple numbers may be needed to represent all the places in the string that it shows up.

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

const letterPositions = function (sentence) {
  const results = {};
  for (let i = 0; i < sentence.length; i++) {
    if (!sentence[i].includes(" ")) {
      if (results[sentence[i]]) {
        results[sentence[i]].push(i);
      } else {
        results[sentence[i]] = [i];
      }
    }
  }
  return results;
};
```

## Explanation

- `letterPositions` takes in a string as its argument.
- It first declares an empty object results that will store the position(s) of each letter in the sentence.
- We then iterate through every character in the `sentence` using a `for...loop`, starting from index `0` and ending at the last index of the `sentence`.
- Every iteration checks if the current character is not a space character `if (!sentence[i].includes(" ")`.
- If it is not a space character, we check if the letter already exists as a property in the `results` object.
- If it does, we push the current index (i) to the array value of the property `results[sentence[i]].push(i)`.
- If it doesn't, we create a new property in the `results` object with the letter as the property name and the value as an array with the current index as the only element `results[sentence[i]] = [i];`.
- Last we return the `results` object which will contain properties for each letter in the sentence and the value for each property is an array of where the letter appears in the `sentence` string.

## Test Cases

```javascript
console.log(letterPositions("lighthouse in the house"));
// output: { l: [ 0 ],  i: [ 1, 11 ], g: [ 2 ], h: [ 3, 5, 15, 18 ], t: [ 4, 14 ], o: [ 6, 19 ], u: [ 7, 20 ], s: [ 8, 21 ], e: [ 9, 16, 22 ], n: [ 12 ] }

console.log(letterPositions("hello"));
// output: { h: [ 0 ], e: [ 1 ], l: [ 2, 3 ], o: [ 4 ] }

assertArraysEqual(letterPositions("hello").h, [0]);
// output: true

assertArraysEqual(letterPositions("hello").e, [1]);
// output: true

assertArraysEqual(letterPositions("hello").l, [2, 3]);
// output: true

assertArraysEqual(letterPositions("hello").o, [4]);
// output: true
```
