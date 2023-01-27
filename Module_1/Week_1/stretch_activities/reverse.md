## Challenge

- Write a program that takes any number of command line arguments, all strings, and reverses them before outputting them one at a time to the console.
- Do NOT use JavaScript's Array.prototype.reverse or Array.prototype.join functions to solve this problem.

## Solution

```javascript
const reverse = function (string) {
  let reversedString = "";
  for (let i = string.length - 1; i >= 0; i--) {
    reversedString += string[i];
  }

  return reversedString;
};
```

## Explanation

- The `reverse` function takes a `string` as an argument
- The function decalres a variable named `reversedString` and assigns it to an empty string.
- It then uses a for loop to iterate over the characters in the string in reverse order (starting from the last character and ending at the first character).
- For each iteration of the loop, the current character of the input string is added to the end of the `reversedString` variable.
- After the loop completes, the final value of the `reversedString` is returned.

## Test Cases

```javascript
console.log(reverse("hey")); // output: yeh
console.log(reverse("lighthouse labs")); // output: sbal esuohthgil
```
