## Challenge

- Make a function that take in a single string as a command line argument and print out an obfuscated version of that password, using the rules defined below:
  - Every "a" in the string should be replaced with a "4".
  - Every "e" in the string should be replaced with a "3".
  - Every "o" (oh) in the string should be replaced with a "0" (zero).
  - Every "l" (el) in the string should be replaced with a "1" (one).

## Solution

```javascript
const password = process.argv[2];

function obfuscate(password) {
  let obfuscatedPassword = "";
  for (let i = 0; i < password.length; i++) {
    if (password[i] === "a") {
      obfuscatedPassword += "4";
    } else if (password[i] === "e") {
      obfuscatedPassword += "3";
    } else if (password[i] === "o") {
      obfuscatedPassword += "0";
    } else if (password[i] === "l") {
      obfuscatedPassword += "1";
    } else {
      obfuscatedPassword += password[i];
    }
  }
  return obfuscatedPassword;
}

console.log(obfuscate(password));
```

## Test Cases

```javascript
node password.js password
// -> p4ssw0rd

node password.js abracadabra
// -> 4br4c4d4br4

node password.js audaciously
// -> 4ud4ci0us1y
```
