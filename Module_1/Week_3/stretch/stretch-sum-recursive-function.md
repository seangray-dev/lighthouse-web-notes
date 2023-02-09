## Challenge

- Make `sum` a recursive function that sums all the whole numbers from `fromN` to `toN`.
- Do not use any loops like `for` or `while`.

## Solution

```javascript
function sum(fromN, toN) {
  if (fromN > toN) {
    return 0;
  }

  return fromN + sum(fromN + 1, toN);
}

console.log(sum(3, 7));
```

## Explanation

- The `sum` is a recursive function that calculates the sum of all integers beteween `fromN` and `toN`.
- The function accepts two parameters: `fromN` and `toN`. We first cheeck if `fromN` is greater than `toN` using an if statement. If this is the case, we return 0, terminating the recursion.
- If `fromN` not is greater than `toN`, we return `fromN` plus the result of calling `sum` agaun with `fromN + 1` and `toN` as arguments. Meaning that each time the function is called, it moves closer to the end condition by incrementing `fromN`.
- The function will continue calling itself this way until `fromN` is greater than `toN`, which will then return 0, ending the the recursion. The result of the the function is the sum of all integers between `fromN` and `toN`.
- In the example `console.log(sum(3,7));` will result in `25`, being the sum of the integers `3 + 4 + 5 + 6 + 7`

## Test Cases

```javascript
describe("sum", function () {
  it("returns 1 when summing 1 to 1", () => {
    expect(sum(1, 1)).to.equal(1);
  });
  it("returns 0 when summing 0 to 0", () => {
    expect(sum(0, 0)).to.equal(0);
  });
  it("returns 5 when summing 5 to 5", () => {
    expect(sum(5, 5)).to.equal(5);
  });
  it("returns 1 when summing 0 to 1", () => {
    expect(sum(0, 1)).to.equal(1);
  });
  it("returns 3 when summing 1 to 2", () => {
    expect(sum(1, 2)).to.equal(3);
  });
  it("returns 25 when summing 3 to 7", () => {
    expect(sum(3, 7)).to.equal(25);
  });
});

sum
  ✓ returns 1 when summing 1 to 1
  ✓ returns 0 when summing 0 to 0
  ✓ returns 5 when summing 5 to 5
  ✓ returns 1 when summing 0 to 1
  ✓ returns 3 when summing 1 to 2
  ✓ returns 25 when summing 3 to 7
```
