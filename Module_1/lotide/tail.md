## Challange

- Create a function tail which returns the "tail" of an array: everything except for the first item (head) of the provided array.
- The tail function should be returning a new array and not modify the original array that is passed in.

## Solution

```javascript
const assertEqual = function (actual, expected) {
  if (actual === expected) {
    return `✅ Assertion Passed: [${actual}] === [${expected}]`;
  } else {
    return `🛑 Assertion Failed: [${actual}] !== [${expected}]`;
  }
};

const tail = function (array) {
  if (array.length <= 1) {
    return [];
  } else {
    return array.slice(1);
  }
};
```

## Explanation

- The `tail` function takes an argument caled `array`.
- It checks if the length of the array is less than or equal to 1.
- If the legnth of the array is equal to or less than 1, it returns an empty array.
- If the length is greater than 1, the function uses the `slice` method to return a new array which contains all the elements from the original array, starting from index 1. Meaning it returns all elements of the array except the first element.

## Test Cases

```javascript
const result = tail(["Hello", "Lighthouse", "Labs"]);

assertEqual(result.length, 2);
// output: ✅ Assertion Passed: [2] === [2]

assertEqual(result[0], "Lighthouse");
// output: ✅ Assertion Passed: [Lighthouse] === [Lighthouse]

assertEqual(result[1], "Labs");
// output: ✅ Assertion Passed: [Labs] === [Labs]

const words = ["Yo Yo", "Lighthouse", "Labs"];
tail(words);
assertEqual(words.length, 3);
// output: ✅ Assertion Passed: [3] === [3]
```
