## Challenge

- Write a function check, which, given a number, returns whether it is valid or not (according to the Luhn Algorithm).

## Solution

```javascript
function luhnCheck(num) {
  let copyOfNum = num;
  // if num is a number, convert to array of numbers
  if (typeof copyOfNum === "number") {
    copyOfNum = Array.from(String(copyOfNum), Number);
  }

  // if even copyOfNum of digits, double every other digit starting from the first
  if (copyOfNum.length % 2 === 0) {
    copyOfNum = copyOfNum.map((digit, i) => (i % 2 === 0 ? digit * 2 : digit));
    // if odd copyOfNum of digits, double every other digit starting from the second
  } else {
    copyOfNum = copyOfNum.map((digit, i) => (i % 2 === 1 ? digit * 2 : digit));
  }

  // if doubled digit is greater than 9, digit is subtracted by 9
  copyOfNum = copyOfNum.map((digit) => (digit > 9 ? digit - 9 : digit));

  // sum all digits
  let sum = copyOfNum.reduce((acc, digit) => (acc += digit), 0);

  // if remainder is 0, from dividing by 10 return true
  return sum % 10 === 0;
}
```
## Explanation

## Test Cases 