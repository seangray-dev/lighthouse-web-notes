## Question 1

Which of the following is true about classes?

## Answer 1

Classes are blueprints (templates) that we use to create ibjects.

## Question 2

Can we create a string using `var word = new String('hello');` in JavaScript? If so, then would it be the same as `var word = 'hello';`?

## Answer 2

Yes, a string can be created using `new String('hello');` but is NOT the same as `'hello'`. The two techniques produce results of different types (object vs. string)

## Question 3

What will the output of the following piece of code be?

```javascript
class Pizza {
  constructor(size, crust) {
    this.size = size;
    this.crust = crust;
    this.toppings = ["cheese"];
  }

  addTopping(topping) {
    this.toppings.push(topping);
  }
}

let pizza = new Pizza("large", "thin");
pizza.addTopping("mushrooms");
console.log(pizza.toppings);
```

## Answer 3

`"cheese", "mushrooms"`. The pizza gets constructed with cheese, then we add mushroom later on.

## Question 4

What is the relationship between these three classes?

```javascript
  class A {
    constructor(name) {
      this.name = name;
    }
  }

  class B extends A {
    ...
  }

  class C extends B {
    ...
  }
```

## Answer 4

`A` is the superclass of `B`, and `B` is the subclass of `A`. `B` is the superclass of `C` and `C` is the subclass of `B`.

That makes `C` a subclass of `A` as well, since it's a subclass of `B`.

## Question 5

When should you use the `super` keyword?

## Answer 5

Use `super` when overriding methods in order to execute the superclass's version of the method. When we override a method, but want the superclass's version of the method to still be called, use super.

## Question 6

What is a benefit of using getter methods instead of accessing value properties directly?

## Answer 6

A getter method allows you to compute a value when the value is needed, rather than alwats keeping track of that value.

## Question 7

What is a benefit of using a setter method instead of accessing value properties directly?

## Answer 7

A correct answer would be that it allows for data validation before updating information.
