## Challenge

- Implement `takeUntil` which will keep collecting items from a provided array until the callback provided returns a truthy value.
- Bring in our `assertArraysEqual` function (and associated `eqArrays` function) in order write some easy-to-read test cases. Since `takeUntil` returns arrays.

## Solution

```javascript
const takeUntil = function (array, callback) {
  let results = [];
  for (let item of array) {
    if (callback(item)) {
      return results;
    }
    results.push(item);
  }
  return results;
};
```

## Explanation

- `takeUntil` takes 2 arguments as inputs `array` and `callback`.
- We create a new empty array named `results` to hold the results.
- We use a `for...of` loop to iterate through each element of the input `array`, and on each element we check whteher the result of applying the callback function is `true` or `false`.
- If the callback function returns `true` we return the `results` array, if the callback returns `false` we push the element onto the `results` array.
- `results` is returned after all elements of the array have been processed before the first time the callback function returned `true`.

## Test Cases

```javascript
// Test 1
const data1 = [1, 2, 5, 7, 2, -1, 2, 4, 5];
const results1 = takeUntil(data1, (x) => x < 0);
console.log(results1); // -> [ 1, 2, 5, 7, 2 ]
console.log(assertArraysEqual(results1, [1, 2, 5, 7, 2])); // -> true

// Test 2
const results2 = takeUntil(data2, (x) => x === ",");
console.log(results2); // -> [ 'I\'ve', 'been', 'to', 'Hollywood' ]
console.log(assertArraysEqual(results2, ["I've", "been", "to", "Hollywood"])); // -> true
```
