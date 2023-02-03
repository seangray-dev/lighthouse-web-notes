## Challenge

- Debug the code and fix any mistakes you find such that the program works correctly.
- Expected Output:

```
node print-in-frame.js
*********
* May   *
* the   *
* force *
* be    *
* with  *
* you   *
*********
***********
* Here's  *
* Johnny! *
***********
**************************************
* Supercalifragalisticexpialadocious *
**************************************
*********
* Lost, *
* like  *
* tears *
* in    *
* the   *
* rain  *
*********
```

## Solution

```javascript
const printInFrame = function (list) {
  list = list.split(" ");
  const longest = longestStr(list).length;
  const border = repeat("*", longest + 4);

  console.log(border);
  for (const word of list) {
    console.log(`* ${word}${repeat(" ", longest - word.length + 1)}*`);
  }
  console.log(border);
};

const repeat = function (str, times) {
  let result = "";

  for (let i = 0; i < times; i++) {
    result += str;
  }

  return result;
};

const longestStr = function (list) {
  let longest = list[0];

  for (const str of list) {
    if (str.length > longest.length) {
      longest = str;
    }
  }

  return longest;
};
```

## Explanation

- The length of the border is too short, to fix this we can increase it by 4.

```javascript
const printInFrame = function (list) {
  list = list.split(" ");
  const longest = longestStr(list).length;
  const border = repeat("*", longest);

  console.log(border);
  for (const word of list) {
    console.log(`* ${word}${repeat(" ", longest - word.length + 1)}*`);
  }
  console.log(border);
};

// Solution

const printInFrame = function (list) {
  list = list.split(" ");
  const longest = longestStr(list).length;
  // added 4 to border
  const border = repeat("*", longest + 4);

  console.log(border);
  for (const word of list) {
    console.log(`* ${word}${repeat(" ", longest - word.length + 1)}*`);
  }
  console.log(border);
};
```

- Initially `repeat` starts with `str` being the `result`, to fix this we can change `result` to be an empty array.

```javascript
const repeat = function (str, times) {
  let result = str;

  for (let i = 0; i < times; i++) {
    result += str;
  }

  return result;
};

// Solution
const repeat = function (str, times) {
  // change result to an empty array
  let result = "";

  for (let i = 0; i < times; i++) {
    result += str;
  }

  return result;
};
```
