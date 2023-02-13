## Challenge

Construct the a function called titleCase that takes a sentence string and gives it title casing.

## Solution

```javascript
const titleCase = function (str) {
  if (str === "") {
    return str;
  }

  const words = str.toLowerCase().split(" ");
  const titleWords = words.map((word) => word[0].toUpperCase() + word.slice(1));
  return titleWords.join(" ");
};
```

## Explanation

- The titleCase takes a single argument `str`
- We then check if the string is an empty string, if it is we return the string immediately.
- If the string is not empty, we the declare a new variable `words` and use the `toLowerCase` and the `split` methods to create a new array containing the words.
- We the declare a new variable `titleWords` and use the `.map` method, we take the first letter of the word `word[0]` and use the `toUpperCase` method on it. We also use the `slice` method to include the word except for the first captialized letter.
- We then return `titleWords` and use the `join(" ")` method to separate the words and convert the array back to a string.

## Test Cases

```javascript
titleCase("this is an example"); // -> "This Is An Example"
titleCase("test"); // -> "Test"
titleCase("i r cool"); // -> "I R Cool"
titleCase("WHAT HAPPENS HERE"); // -> "What Happens Here"
titleCase(""); // -> ""
titleCase("A"); // -> "A"
```
