## Challenge

- Implement the definition for function eqObjects which will take in two objects and returns true or false, based on a perfect match.

## Solution

```javascript
const eqObjects = function (object1, object2) {
  // check if the number of keys in both objects are of the same length
  if (Object.keys(object1).length !== Object.keys(object2).length) {
    return false;
  }

  // loop through object1 keys
  for (const key in object1) {
    // check if current value of current key is an object
    if (typeof object1[key] === "object" && object1[key] !== null) {
      // recursively call the object if it is an object
      return eqObjects(object1[key], object2[key]);
    }
    // if object 2 doens't have same key, return false
    if (!object2.hasOwnProperty(key)) {
      return false;
    }
    // check if both objects' keys are arrays
    if (Array.isArray(object1[key]) && Array.isArray(object2[key])) {
      // if they are, use eqArrays to compare the arrays
      if (!eqArrays(object1[key], object2[key])) {
        return false;
      }
      // if values of keys are not the same return false
    } else if (object1[key] !== object2[key]) {
      return false;
    }
  }
  // return true if all checks pass
  return true;
};
```

## Explanation

- `eqObjects` compares two objects determing if they are equal or not. It takes in two objects as parameters `object1` and `object2`.
- First we check if the number of keys in both objects are the same length, if they arent we immeditaely return `false`,
- We then loop through each key in `object1` and for each key, we check if the value of that key is an object, if it is we recursively call the function of both `object1[key]` & `object2[key]` allowing to check for nested objects.
- If `object2` doesn't have the same key we return `false`
- If both `object1[key]` & `object2[key]` are arrays, the function uses the `eqArrays` function to compare them, if they are not equal, we return `false`
- If `object1[key]` and `object2[key]` are not both arrays, and not equal to one another, we return `false`.
- If all checks passed we can confirm the two obejcts are equal, and return `true`.

## Test Cases

```javascript
eqObjects({ a: { z: 1 }, b: 2 }, { a: { z: 1 }, b: 2 }); // => true
eqObjects({ a: { y: 0, z: 1 }, b: 2 }, { a: { z: 1 }, b: 2 }); // => false
eqObjects({ a: { y: 0, z: 1 }, b: 2 }, { a: 1, b: 2 }); // => false
```
