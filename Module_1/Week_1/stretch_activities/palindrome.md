## Challenge

- Debug the issue in the isPalindrome function.
- **Bonus:** There's another issue to debug in the isPalindrome function. You may attempt to solve this stretch bug by uncommenting the bonus assertions at the bottom.

## Solution

```javascript
const isPalindrome = function (str) {
  // convert the string to lowercase
  const noSpaces = str.toLowerCase().split(" ").join("");
  const midIndex = Math.floor(noSpaces.length / 2);
  const lastIndex = noSpaces.length - 1;

  for (let i = 0; i < midIndex; i++) {
    if (noSpaces[i] !== noSpaces[lastIndex - i]) {
      return false;
    }
  }
  // added the return statement
  return true;
};
```

## Explanation

- `isPalindrome` intially didn't have a return statment to indicate if the `isPalindrome` was successful. Therefore it would always return `undefined`.
- In order for us to check a string with case sensitivity we need to convert the string to lowercase using the `toLowerCase()` method.

## Test Cases

```javascript
const assertPalindrome = function (word, expected) {
  console.log(`Testing isPalindrome(\"${word}\"):`);
  const actual = isPalindrome(word);
  if (actual === expected) {
    console.log("\x1b[32m%s\x1b[0m", `\tPASS ✅ function returned ${actual}\n`);
    return true;
  } else {
    console.log(
      "\x1b[31m%s\x1b[0m",
      `\tFAIL 🛑 function returned ${actual} (expected ${expected})\n`
    );
    return false;
  }
};

assertPalindrome("p", true);
// -> true
assertPalindrome("racecar", true);
// -> true
assertPalindrome("my gym", true);
// -> true
assertPalindrome("foo", false);
// -> true
assertPalindrome("fluff", false);
// -> true
assertPalindrome("just some random words", false);
// -> true

// Bonus:
assertPalindrome("Kayak", true);
// -> true
assertPalindrome("a santa at NASA", true);
// -> true
```
