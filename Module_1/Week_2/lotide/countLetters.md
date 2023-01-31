## Challenge

- The function should take in a sentence (as a string) and then return a count of each of the letters in that sentence.
- For example, `countLetters('LHL')` should return results indicating that `L` appears twice, and `H` once.

## Solution

```javascript
const countLetters = function (string) {
  let results = {};
  for (letter of string) {
    if (letter !== " ") {
      if (results[letter]) {
        results[letter] += 1;
      } else {
        results[letter] = 1;
      }
    }
  }
  return results;
};
```

## Explanation

- `countLetters` takes a string as an argument and returns an object containg the counts of each letter from the input string.
- We declare an empty object called `results`
- We use a `for...of` loop to iterate over every `letter` of the input string.
- We use an `if` statement to check if the current character is not a space (`letter !== " "`), and if the current character is not a space the function continues.
- We use another `if` statement to check if the current character already exists in the `results` object. If if does then we increment the count by 1.
- If the current character does not exist in the `results` object we create a new key-value pair added to the results object, with the character being the key and 1 as the value.
- When the loop finishes we return the `results` object.

## Test Cases

```javascript
console.log(countLetters("lighthouse in the house"));

// output: { l: 1, i: 2, g: 1, h: 4, t: 2, o: 2, u: 2, s: 2, e: 3, n: 1 }
```
