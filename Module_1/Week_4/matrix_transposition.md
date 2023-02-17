## Challenge

You'll be implementing a function called transpose, which will receive an array of arrays as its only parameter. Your function must return a new array with the columns and rows switched. Note that we've included a printMatrix function, which nicely prints out your 2D arrays.

## Solution

```javascript
const transpose = function (matrix) {
  // declare a variable to store the result
  const result = [];
  // loop over the columns in the matrix
  for (let i = 0; i < matrix[0].length; i++) {
    // creating a new array to store the elements of the current column
    result[i] = [];
    // loop over the rows in the matrix
    for (let j = 0; j < matrix.length; j++) {
      // copy current element to current column of result
      result[i][j] = matrix[j][i];
    }
  }
  return result;
};
```

## Explanation

- The `transpose` function takes in a 2d array `matrix`
- We declare an empty array `result` to store the transpose of the input matrix
- We loop over the columns of the input matrix using a `for loop` running from 0 to the number of columns in the matrix (`matrix[0].length`)
- For each column, we create a new array in `result` to store the elements of that column
- We then loop over the rows of the input matrix using another `for loop` that runs from 0 to the number of rows in the matrix (`matrix.length`)
- For each element in the current row and column of the input matrix, it copies the value to the corresponding row and column of the `result` array
- Once all elements have been copied to `result` we return it.

## Test Cases

```javascript
printMatrix(
  transpose([
    [1, 2, 3, 4],
    [1, 2, 3, 4],
    [1, 2, 3, 4],
    [1, 2, 3, 4],
  ])
);

// Output:
// 1 1 1 1
// 2 2 2 2
// 3 3 3 3
// 4 4 4 4

printMatrix(
  transpose([
    [1, 2],
    [3, 4],
    [5, 6],
  ])
);

// Output:
// 1 3 5
// 2 4 6

printMatrix(transpose([[1, 2, 3, 4, 5, 6, 7]]));

// Output:
// 1
// 2
// 3
// 4
// 5
// 6
// 7
```

## Alternative Solution & Explanation

```javascript
const transpose = function (matrix) {
  return matrix[0].map((_, i) => matrix.map((row) => row[i]));
};
```
- The function calls `map` on the first row of the input matrix `matrix[0]`, this will return a new array of the same length as the original array, where every element is the result of calling the provided callback function on each element of the original array. In this case, the callback function takes 2 arguments: the current element (ignored with `_` placeholder) and the index of the current element `i`.
- For each index `i` of the first row, the callback function mpas the elements of each row in the input matrix using another `map` method. This also returns a new array of the same length of the original array. In this case, the provided function takes only one argument of `row` being the current row. 
- For each `row`, the callback function returns the element of `row` at index `i` corresponding to the element at row `i` and column `j` which results in the array containing elements of the first column. 
- The `map` method being used on the input matrix `matrix[0]` returns an array of arrays, where each array corresponds to a column of the input matrix.  