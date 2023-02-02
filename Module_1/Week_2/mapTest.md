## Challenge

- Use the `map` method on `lighthouses` so that we instead see an array of numbers.

## Solution

```javascript
const lighthouses = [
  "Gibraltar Point",
  "Peggy's Point",
  "Cove Island",
  "Discovery Island",
  "Cape Scott",
  "Point Clark",
  "Kincardine",
];

lighthouses.map((lighthouse) => lighthouse.length);
// -> [ 15, 13, 11, 16, 10, 11, 10 ]
```

## Explanation
- `lighthouses.map((lighthouse) => lighthouse.length);` takes an array of strings from `lighthouses` and returns a new array containing the length of each string in the original array.
- `.map()` is a higher-order-function that creates a new array by transforming each element of the original array using the callback function given.
- In this case the callback function is `(lighthouse) => lighthouse.length` returning the length of the string passed from the argument `lighthouse`.
- The new array contains the length of each string in `lighthouses` in the exact same order as the original array. 