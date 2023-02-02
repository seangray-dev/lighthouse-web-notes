## Challenge

- Refactor the code from `findWaldo.js`
- We should find our resulting code making no more reference to a named actionWhenFound function. It should instead declare and pass that behavior anonymously into findWaldo, all in one go!

## Solution

```javascript
const findWaldoAnon = function (names, found) {
  names.forEach((name, index) => {
    if (name === "Waldo") {
      found(index);
    }
  });
};

findWaldoAnon(["Alice", "Bob", "Waldo", "Winston"], (index) => {
  console.log(`Found Waldo at index ${index}!`);
});
```

## Explanation

- `findWaldoAnon` takes 2 arguments: `names` (an array of names) and `found` (a callback function).
- We use a `forEach` method looping through the `names` array, on each iteration we check if the current name is equal to `"Waldo"`. If it is, we `invoke` the `found` callback function, passing the current index as the argument.
- We pass a anonymous function (a function w/o a name) to `findWaldoAnon` as the `found` argument, which logs a message to the console, saying at which index `"Waldo"` was found.

## Text Cases

```javascript
findWaldoAnon(["Alice", "Bob", "Waldo", "Winston"], (index) => {
  console.log(`Found Waldo at index ${index}!`);
}); // -> Found Waldo at index 2!
```
