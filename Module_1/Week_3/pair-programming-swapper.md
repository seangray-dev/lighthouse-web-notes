## Challenge

- In this exercise, you will write a function that will swap values between two objects. Your function will receive four parameters:
  - `key1`, a string
  - `object1`, an object
  - `key2`, a string
  - `object2`, an object
- Your function should:

- fetch the value stored in `key1` in `object1`, and then store that value in `key2` of `object2`.
- take the original value stored in `key2` of `object2`, and store that in `key1` of `object1`.
- not need to return anything.

## Solution

```javascript
const swapper = function (key1, object1, key2, object2) {
  console.log("Swap!");

  let temp = object1[key1];

  object1[key1] = object2[key2];
  object2[key2] = temp;

  console.log("object1: ", object1);
  console.log("object2: ", object2);
};
```

## Explanation

- Inside of the function we first log `"Swap!"` to the console.
- We declare a local variable called `temp` and assigns it the value of `object1[key1]`
- We assign the value of `object2[key2]` to `object1[key1]`
- We assing the value of `temp` to `object2[key2]`
- Lastly, we log the values of both `object1` and `object2` to the console.
- We can access the properties of an object using square bracket notation which allows us to access the properties of an object using a string.

## Test Cases

```javascript
swapper("a", { a: 1, b: 2, c: 3 }, "c", { a: 4, b: 3, c: 5 });
/* -> 
Swap!
object1: { a: 5 , b: 2, c: 3 }
object2: { a: 4, b: 3, c: 1 }
*/
swapper("b", { a: 8, b: 7, c: 6 }, "d", { a: 5, b: 1, c: 2, d: 12 });
/* -> 
Swap!
object1: { a: 8 , b: 12, c: 6 }
object2: { a: 5, b: 1, c: 2, d: 7}
*/
swapper("c", { a: 1, b: 3, c: 3, d: 7 }, "c", { a: 4, b: 0, c: 5 });
/* -> 
Swap!
object1: { a: 1 , b: 3, c: 5, d: 7 }
object2: { a: 4, b: 0, c: 3 }
*/
```
