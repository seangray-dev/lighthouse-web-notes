# Quiz

## Question #1:

### In programming, what is meant by the term First-class citizen (or First-class object)?

## Answer:

- An object with no restrictions on it's creation, destruction, or usage. Including the ability to be passed as an argument, retruend from a function and assigned to a variable.

## Question #2:

### Can functions act as objects in JavaScript?

## Answer:

- Functions are instances of the Object type in Javascript and can nhave properties and methods just like any other object.

## Question #3:

### Considering the following JavaScript code, is it possible to assign attributes to a function?

```javascript
const funObject = function () {
  console.log("I am function.");
};
funObject.someAttribute = 42;
```

## Answer:

- It is possible because JavaScript functions are also Objects. Functions can be assigned attributes like any other object.
