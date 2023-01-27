## Challenge

- Write a program that takes a single parameter from the command line, a number, and rolls that many six-sided dice.

## Solution

```javascript
const rollDice = function (num) {
  let result = [];
  for (let i = 0; i < num; i++) {
    let roll = Math.floor(Math.random(1) * 6) + 1;
    result.push(roll);
  }
  return result;
};

console.log(rollDice(3));
// output: [6, 2, 5]
```

## Explanation

- The function takes in a single argument `num` which represents the number of dice rolls we want to simulate.
- We initialize an empty array called `result` which we will use to store the result of the dice rolls.
- We then use a for loop to sumulate the amount of dice rolls.
- On each iteration, a new random number between 1 & 6 is generated using the `Math.random` function.
- We use the `Math.floor` to round down to the nearest whole number.
- The number is then pushed to the `result` array using the the `push` method.
- Finally we return the `result` array contianing all of the simulated dice rolls.
