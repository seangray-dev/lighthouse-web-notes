## Challenge

- Write a function that joins the contents of `conceptList` together into one string.
- `concepts`, with each list item separated from the previous by a comma.
- To implement this we'll create a `joinList` function which will take in any array of strings and return a comma-separated string.
- **Note: We can NOT use the built-in Array join function.**

## Solution

```javascript
const joinList = function (array) {
  let result = "";
  for (let i = 0; i < array.length; i++) {
    result += array[i];
    if (i < array.length - 2) {
      result += ", ";
    } else if (i === array.length - 2) {
      result += " & ";
    }
  }
  return result;
};
```

## Explanation

- The `joinList` function, takes in an argument called `array`.
- It declares an empty string variable called `result`
- A for-loop if used to iterate over the elements of the array, starting from the first element (index 0) and going until the last element.
- On each iteration, the current element of the array is added to the `result` variable, and a comma and space are added after it.
- The if statement checks if the current iteration is not the second last one in the array.
- If it isn't, it adds a comma and space after the current element, otherwise it doesn't.
- The else if statement checks if the current iteration is the second last element in the array and adds `&` before it.
- It the returns the final string containing all the elements of the array together, separated by commas and spaces but without a final trailing comma.

## Test Cases

```javascript
const conceptList = [
  "gists",
  "types",
  "operators",
  "iteration",
  "problem solving",
];
const concepts = joinList(conceptList);
console.log(`Today I learned about ${concepts}.`);

// output: Today I learned about gists, types, operators, iteration & problem solving.
```
