## Challenge

- Implement middle which will take in an array and return the middle-most element(s) of the given array.
- The middle function should return an array with only the middle element(s) of the provided array. This means that the length of the returned elements could vary.
- For arrays with one or two elements, there is no middle. Return an empty array.
- For arrays with odd number of elements, an array containing a single middle element should be returned.
- For arrays with an even number of elements, an array containing the two elements in the middle should be returned

## Solution

```javascript
const middle = function (array) {
  if (array.length <= 2) {
    return [];
  }
  if (array.length % 2 === 0) {
    return [array[array.length / 2 - 1], array[array.length / 2]];
  } else {
    return [array[Math.floor(array.length / 2)]];
  }
};
```

## Explanation

- The `middle` function takes an `array` as an argument.
- If the length of the array is less than or equal to 2, it returns an empty array.
- If the length of the array is even, it returns an array containing:
  - the element at the middle index -1
  - the element at the middle index
- If the length of the array is odd, it returns an array containing:
  - the element at the middle index
- The middle index is determined by using the floor division operator (`/`) and the `Math.floor()` function to find the middle index(s) of the array.

## Test Cases

```javascript
middle([1]); // => []
middle([1, 2]); // => []
middle([1, 2, 3]); // => [2]
middle([1, 2, 3, 4, 5]); // => [3]
middle([1, 2, 3, 4]); // => [2, 3]
middle([1, 2, 3, 4, 5, 6]); // => [3, 4]
```
