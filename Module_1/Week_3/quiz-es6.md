## Question 1:

- Given the following JavaScript code, what will be the resulting value of url?

```javascript
let PORT = 8080;
let url = `http://localhost:${PORT}/path`;
```

## Answer:

- `http://localhost:8080/path` the port will be interpolated into the template literal

## Question 2:

- Considering the following JavaScript code, what will the console output be and why?

```javascript
const foo = function () {
  var x = 1;
  if (x === 1) {
    let y = 2;
  }
  console.log("Value of y is " + y);
};
foo();
```

## Answer:

- the block-scoping of let y = 2 makes it available only within the if statement block

## Question 3:

- Consider the following JavaScript code, what would be the console output?

```javascript
const names = ["Graham"];
names = [];
console.log(names);
```

## Answer:

- Console would show a `TypeError: Assignment to constant variable` due to the declaration using `const`.

## Question 4:

- Given the following JavaScript code, what would be the console output?

```javascript
const names = [];
names.push("Jordan");
console.log(names);
```

## Answer:

- Console would show `['Jordan']`, it sitll allows us to change the value of the referenced variable.

## Question 5:

- How are Arrow Functions () => {} different than traditional function expressions?

## Answer:

- Arrow Functions do not declare their own scope, arrow functions inherit parent scope
