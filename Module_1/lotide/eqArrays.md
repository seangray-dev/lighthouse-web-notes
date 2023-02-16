## Challenge

- Implement a function eqArrays which takes in two arrays and returns true or false, based on a perfect match.

## Solution

```javascript
const eqArrays = function (arr1, arr2) {
  if (!Array.isArray(arr1) || !Array.isArray(arr2)) {
    return false;
  }
  if (arr1.length !== arr2.length) {
    return false;
  }

  for (let i = 0; i < arr1.length; i++) {
    if (Array.isArray(arr1[i]) && Array.isArray(arr2[i])) {
      if (!eqArrays(arr1[i], arr2[i])) {
        return false;
      }
    } else if (arr1[i] !== arr2[i]) {
      return false;
    }
  }
  return true;
};
```

## Explanation

- `eqArrays` is used to compare two arrays and return true if they have the same values in the same order, it takes in two parameters `arr1` and `arr2`.
- We first check if either inputs are not arrays, and if they aren't we return `false`.
- We then check if the arrays have the same length, if they do not we return `false`.
- If the arrays are the same length, we then loop through eah item in `arr1` and for each item in the array we check if both `arr1[i]` and `arr2[i]` are arrays, we use recursion to call `eqArrays` again with the sub-arrays as arguments. If the the nested arrays aren't equal we return `false`.
- If `arr1[i]` and `arr2[i]` are not both arrays anf aren't equal to one another, we return `false`.
- If all checks pass, we return `true`.

## Test Cases

```javascript
eqArrays([[2, 3], [4]], [[2, 3], [4]]) // => true
eqArrays([[2, 3], [4]], [[2, 3], [4, 5]) // => false
eqArrays([[2, 3], [4]], [[2, 3], 4]) // => false
```
