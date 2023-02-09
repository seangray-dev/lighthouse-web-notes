## Challenge

- Make sumItems a function that sums all the numbers in an array. So if you input the array `[1, 2, 3, 4, 5]`, the function will return `15`. This will be your base case.
- Modify your function so that your input array can contain either numbers or arrays of numbers with no limit to the number of nested arrays. So if you input the array `[[1, 2, [[3], 4]], 5, []]`, the function will return `15`. This will be the recursive case and require you to call the same function from within.

## Solution

```javascript
function sumItems(array) {
  let sum = 0;
  for (num of array) {
    if (!Array.isArray(num)) {
      sum += num;
    } else {
      sum += sumItems(num);
    }
  }
  return sum;
}
```

## Explanation

- `sumItems` is a recursive function that takes an array as input and returns the sum of all the values contained in the array, including nested arrays.
- The function intializes a variable `sum` to 0, which will keep track of the total value.
- We then use a `for...of` loop to iterate over the input `array`.In each item in the `array`, we check if it is an array using the `Array.isArray` method. If it is an array, the function calls itself with that item as the argument, repeating the process for the nested arrays.
- If the item is not an array, we add it to `sum`.
- We then return the `sum` which contains the sum of all values in the input array and any nested arrays.

## Test Cases

```javascript
sumItems([25]);
sumItems([1, 3, 3, 5, 5]); // -> 17
sumItems([[1, 2, [[3], 4]], 5, []]); // -> 15
sumItems([[[5], [[[4]]], [[3], 2]], 1, []]); // -> 15

✓ handles a single item array fine
✓ handles no nested arrays fine
✓ handles four levels of nesting fine
✓ handles even more levels of nesting fine

```
