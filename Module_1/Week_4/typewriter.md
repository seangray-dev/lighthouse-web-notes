## Challenge

- Our goal is to animate the sentence, revealing one character at a time. This would make it look as though it is being typed in by someone.

## Solution

```javascript
const sentence = "hello there from lighthouse labs";
let delay = 0;

for (const char of sentence) {
  setTimeout(() => {
    process.stdout.write(char);
  }, delay);
  delay += 50;
}

setTimeout(() => {
  process.stdout.write("\n");
}, delay);
```

## Explanation

This code uses a `for...o`f`loop and`setTimeout()` function to animate the printing of the sentence string to the console.

The sentence variable holds the string `"hello there from lighthouse labs"`, which is the text that will be printed.

The `let delay = 0` statement initializes a variable `delay` to 0, which will be used to delay the printing of each character in the `sentence`.

The `for...of loo`p iterates through each character in the sentence string. For each character, a `setTimeout()` function is called with a callback function that prints the character to the console using `process.stdout.write(char)`. The delay between printing each character is calculated based on the value of `delay` and incremented by 50ms for each character, so that each character is printed with a slightly longer delay than the previous character.

Finally, after all the characters have been printed, another `setTimeout()` function is called with a callback function that prints a newline character to the console using `process.stdout.write("\n")`. This adds a newline to the end of the printed text to make sure the next line of output starts on a new line.
