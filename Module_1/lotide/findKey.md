## Challenge

- Implement the function `findKey` which takes in an object and a callback. It should scan the object and return the first key for which the callback returns a truthy value. If no key is found, then it should return undefined.

## Solution

```javascript
const findKey = function (obj, callback) {
  for (let key in obj) {
    if (callback(obj[key])) {
      return key;
    }
  }
  return undefined;
};
```

## Explanation

- `findKey` takes in 2 arguments: `obj` and `callback`.
- We use a `for...in` loop to iterate through the properties of the object.
- For each property, we apply a callback function with the value of the property as the argument. When the callback returns a `truthy` value, we immediately return the name of the property.
- If the loop cimpletes and the callback function did not return a `truthy` value we return `undefined`.

## Test Cases

```javascript
const planets = findKey(
  {
    "Blue Hill": { stars: 1 },
    Akaleri: { stars: 3 },
    noma: { stars: 2 },
    elBulli: { stars: 3 },
    Ora: { stars: 2 },
    Akelarre: { stars: 3 },
  },
  (x) => x.stars === 2
); // -> "noma"

console.log(assertEqual(planets, "noma"));
// -> ✅ Assertion Passed: [noma] === [noma]
```
