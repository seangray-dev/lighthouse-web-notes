## Challenge

- Implement the function `findKeyByValue` which takes in an object and a value. It should scan the object and return the first key which contains the given value. If no key with that given value is found, then it should return `undefined`.

![findKeyByValue](./images/lotide-objects-findKey.png)

## Solution

```javascript
const assertEqual = function (actual, expected) {
  if (actual === expected) {
    return `✅ Assertion Passed: [${actual}] === [${expected}]`;
  } else {
    return `🛑 Assertion Failed: [${actual}] !== [${expected}]`;
  }
};

function findKeyByValue(obj, value) {
  for (let key of Object.keys(obj)) {
    if (obj[key] === value) {
      return key;
    }
  }
  return undefined;
}
```

## Explanation

- The `findKeyByValue` function takes 2 arguments: `obj` and `value`.
- To get the keys of `obj` we used `Object.keys(obj)` and then used a `for...of` loop to iterate over the keys of the `obj` object.
- We then check if the the `obj[key]` is equal to the `value`, if the values are equal, immediately we `return` the `key`.
- If none of the values match, we return `undefined` after the loop.

## Test Cases

```javascript
const bestTVShowsByGenre = {
  sci_fi: "The Expanse",
  comedy: "Brooklyn Nine-Nine",
  drama: "The Wire",
};

assertEqual(findKeyByValue(bestTVShowsByGenre, "The Wire"), "drama");
// output: ✅ Assertion Passed: [drama] === [drama]
assertEqual(findKeyByValue(bestTVShowsByGenre, "That '70s Show"), undefined);
// output: ✅ Assertion Passed: [undefined] === [undefined]
```
