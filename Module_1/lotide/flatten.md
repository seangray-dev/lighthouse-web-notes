## Challenge

- Create a function `flatten` which will take in an array containing elements including nested arrays of elements, and return a "flattened" version of the array.
- **NOTE: typeof for arrays returns "object":**

## Solution

```javascript
const flatten = function (array) {
  const flattenedArray = [];
  if (Array.isArray(array)) {
    return flattenedArray.concat(...array);
  } else {
    return `This is not an array`;
  }
};
```

## Explanation

- The `flatten` function takes in a single parameter `array`.
- The function declares an empty array called `flattendArray`.
- If then uses the `isArray` method to check if the `array` passed as an argument is an array or not.
- If it is an array it uses the `concat` method with the spread operator (`...`) to flatten the array and return the flattened array.
- The spread operator (`...`) is used to spread the elements of nested array into the `flattenedArray` and concatenate them.
- If it is not an array, it returns the string `"This is not an array"`.
- This function is used to flatten an array of arrays into a single array.

## Test Cases

```javascript
console.log(flatten([1, 2, [3, 4], 5, [6]])); // output: [ 1, 2, 3, 4, 5, 6 ]
console.log(flatten({})); // output: "This is not an array"
```
