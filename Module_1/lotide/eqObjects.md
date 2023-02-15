## Challenge

- Implement the definition for function eqObjects which will take in two objects and returns true or false, based on a perfect match.

## Solution

```javascript
const eqArrays = function (actual, expected) {
  if (actual.length !== expected.length) {
    return false;
  } else {
    for (let i = 0; i < actual.length; i++) {
      if (actual[i] !== expected[i]) {
        return false;
      }
    }
    return true;
  }
};

const assertEqual = function (actual, expected) {
  if (actual === expected) {
    return `✅ Assertion Passed: [${actual}] === [${expected}]`;
  } else {
    return `🛑 Assertion Failed: [${actual}] !== [${expected}]`;
  }
};

const eqObjects = function (object1, object2) {
  // check if the number of keys in both objects are of the same length
  if (Object.keys(object1).length !== Object.keys(object2).length) {
    return false;
  }
  // loop through object1 keys
  for (const key in object1) {
    // check if both objects' keys are arrays
    if (Array.isArray(object1[key]) && Array.isArray(object2[key])) {
      // if they are, use eqArrays to compare the arrays
      if (!eqArrays(object1[key], object2[key])) {
        return false;
      }
    } else if (object1[key] !== object2[key]) {
      return false;
    }
  }

  return true;
};
```

## Explanation

- `eqObjects` compares two objects determing if they are equal or not.
- First we check if `object1[key]` and `object2[key]` are arrays, by using the `eqArrays` function to compare them. If they are not equal, we return `false`.
- Second if both `object1[key]` and `object2[key]` are not arrays, we compare the values of `object1[key]` and `object2[key]` using the equality operator `!==`. If they are not equal, we return `false`
- If both of these checks pass, then we return `true`.

## Test Cases

```javascript
const shirtObject = { color: "red", size: "medium" };
const anotherShirtObject = { size: "medium", color: "red" };
eqObjects(shirtObject, anotherShirtObject); // -> true
assertEqual(eqObjects(shirtObject, anotherShirtObject), true);
// -> ✅ Assertion Passed: [true] === [true]

const longSleeveShirtObject = {
  size: "medium",
  color: "red",
  sleeveLength: "long",
};
eqObjects(shirtObject, longSleeveShirtObject); // -> false
assertEqual(eqObjects(shirtObject, longSleeveShirtObject), false);
// -> ✅ Assertion Passed: [false] === [false]

const student1 = { subjects: ["math", "science"] };
const student2 = { subjects: ["math", "science"] };

eqObjects(student1, student2); // -> true
assertEqual(eqObjects(student1, student2), true);
// -> ✅ Assertion Passed: [true] === [true]
```
