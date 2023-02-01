## Challenge

### Exercise 1

- Modify the callback function in the previous example so that it accepts a single argument `index` and logs it. The problem should therefore output something like "Found Waldo at index 2!".

### Exercise 2

- Refactor the function `findWaldo` to use the `forEach()` method instead of a `for` loop.

## Solution

### Exercise 1

```javascript
const findWaldo = function (names, found) {
  for (let i = 0; i < names.length; i++) {
    let name = names[i];
    if (name === "Waldo") {
      found(i); // execute callback and pass the index
    }
  }
};

const actionWhenFound = function (index) {
  console.log(`Found Waldo at index ${index}!`);
  // -> Found Waldo at index 2!
};

findWaldo(["Alice", "Bob", "Waldo", "Winston"], actionWhenFound);
// -> undefined
```

### Exercise 2

```javascript
const findWaldo2 = function (names, found) {
  names.forEach((name, index) => {
    if (name === "Waldo") {
      found(index);
    }
  });
};

const actionWhenFound2 = function (index) {
  console.log(`Found Waldo at index ${index}!`);
  // -> Found Waldo at index 2!
};

findWaldo(["Alice", "Bob", "Waldo", "Winston"], actionWhenFound);
// -> undefined
```

## Explanation

### Exercise 1

- `findWaldo` accepts two arguments `names` and `found`.
- We use a `for` loop to iterate over the `names` array, and for each name we check if it is equal to `"Waldo"` in the array as an argument (`i`)
- The `actionWhenFound` function is called as the `found` callback, taking one argument: `index` and logs the index of `"Waldo"`.

### Exercise 2

- `findWaldo2` accepts two arguments `names` and `found`.
- We use a `forEach` loop to go through the `names` array. `forEach` method takes a callback function as an argument to run on each element in the array. The callback function is the arrow function `(name, index) => {...}` which takes two arguments, `names` and `index`. `name` being the current element in the array, and `index` being the index.
- We check if the current `name` is equal to `Walso` and if so, we call the `found` function and pass the `index` as the argument. `found` is another callback that was passed to `findWaldo2` function.
- The `actionWhenFound2` function is called as the `found` callback, taking one argument: `index` and logs the index of `"Waldo"`.
- `findWaldo2` is called passing in an array of names and the `actionWhenFound2` callback function.
