## Implementing assertEqual

- Make the function compare the two values it takes in and print out a message telling us if they match or not.
- If the values match, it should print (`console.log`) the following: `Assertion Passed: [actual] === [expected]` (but with the values filled in)
- Otherwise it should print (`console.log`) the following: `Assertion Failed: [actual] !== [expected]` (but with the values filled in)
- Write out a few calls to it and confirm that it is indeed working as expected.

- Test at least the following scenarios:
  - Comparing identical strings
  - Comparing non-identical strings
  - Comparing identical numbers
  - Comparing non-identical numbers

## Solution

```javascript
const assertEqual = function (actual, expected) {
  if (actual === expected) {
    return `✅ Assertion Passed: [${actual}] === [${expected}]`;
  } else {
    return `🛑 Assertion Failed: [${actual}] !== [${expected}]`;
  }
};
```

## Explanation

- The function takes in 2 arguments `actual` and `expected`
- It uses the strict equality operator (`===`) to compare the 2 values as arguments.
- If the arguments are equal, the function returns a string says `Assertion Passed` and the values being compared.
- If the values are not equal, it returns a string `Assertion Failed` and the values being compared.

## Test Cases

```javascript
console.log(assertEqual(1, 1));
// output: ✅ Assertion Passed: [1] === [1]

console.log(assertEqual(true, true));
// output: ✅ Assertion Passed: [true] === [true]

console.log(assertEqual(false, !true));
// output: ✅ Assertion Passed: [false] === [false]

console.log(assertEqual("Lighthouse Labs", "Bootcamp"));
// output: 🛑 Assertion Failed: [Lighthouse Labs] !== [Bootcamp]

console.log(assertEqual(2, "2"));

// output: 🛑 Assertion Failed: [2] !== [2]

console.log(assertEqual("LABS", "labs"));
// output: 🛑 Assertion Failed: [LABS] !== [labs]
```
