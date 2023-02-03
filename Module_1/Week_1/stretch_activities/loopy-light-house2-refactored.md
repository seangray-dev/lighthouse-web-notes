## Challenge

- If you haven't already, complete the stretch exercise in the Loopy Lighthouse activity. Once you're done, sit with a fellow student who has also finished the stretch exercise and refactor the code together. Figure out how to reduce repetitive code and how to make your solution as general as possible.

```javascript
function loopyLighthouse(range, multiples, words) {
  const start = range[0];
  const end = range[1];
  const multiple1 = multiples[0];
  const multiple2 = multiples[1];
  const word1 = words[0];
  const word2 = words[1];

  for (let i = start; i <= end; i++) {
    if (i % multiple1 === 0 && i % multiple2 === 0) {
      console.log(word1 + word2);
    } else if (i % multiple1 === 0) {
      console.log(word1);
    } else if (i % multiple2 === 0) {
      console.log(word2);
    } else {
      console.log(i);
    }
  }
}
```

## Solution

```javascript
function loopyLighthouse(range, multiples, words) {
  const [start, end] = range;
  const [multiple1, multiple2] = multiples;
  const [word1, word2] = words;

  for (let i = start; i <= end; i++) {
    let output = "";
    if (i % multiple1 === 0) {
      output += word1;
    }
    if (i % multiple2 === 0) {
      output += word2;
    }
    console.log(output || i);
  }
}
```

## Explanation

- We can destructuring to extract elements from the `range`,`multiples` and `words` arrays.

```javascript
const start = range[0];
const end = range[1];
const multiple1 = multiples[0];
const multiple2 = multiples[1];
const word1 = words[0];
const word2 = words[1];

// Solution
const [start, end] = range;
const [multiple1, multiple2] = multiples;
const [word1, word2] = words;
```

- We can also simplify the conditional logic

```javascript
for (let i = start; i <= end; i++) {
  if (i % multiple1 === 0 && i % multiple2 === 0) {
    console.log(word1 + word2);
  } else if (i % multiple1 === 0) {
    console.log(word1);
  } else if (i % multiple2 === 0) {
    console.log(word2);
  } else {
    console.log(i);
  }
}

// Solution
for (let i = start; i <= end; i++) {
  let output = "";
  if (i % multiple1 === 0) {
    output += word1;
  }
  if (i % multiple2 === 0) {
    output += word2;
  }
  console.log(output || i);
}
```
