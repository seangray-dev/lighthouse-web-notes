## Example 1

```javascript
let countDownFrom = (num) => {
  if (num === 0) return;
  console.log(num);
  countDownFrom(num - 1);
};

countDownFrom(10);
```

## Explanation for Example 1

- The `countDownFrom` function takes a number as an argument and prints each number from the input down to 0.
- The function uses recursion to repeatedly call itself with a reduced number until the number reaches 0. We use an if statement to check if the input `num` is eqaul to 0. If it is, the function returns without any further processing.
- If `num` is not equal to 0, the function uses `console.log();` to print the value of `num` and then calls itself again with `num - 1` as the argument. Effectively reducing the value of `num` by 1 on eaach iteration of the function until `num` reaches 0, and the function returns.
- In the example `countDownFrom(10)`, the function is called with the argument of `10` logging the numbers from 10, down to 1 to the console.

## Example 2

```javascript
let categories = [
  { id: "animals", parent: null },
  { id: "mammals", parent: "animals" },
  { id: "cats", parent: "mammals" },
  { id: "dogs", parent: "mammals" },
  { id: "chihuahua", parent: "dogs" },
  { id: "labrador", parent: "dogs" },
  { id: "persian", parent: "cats" },
  { id: "siamese", parent: "cats" },
];

let makeTree = (categories, parent) => {
  let node = {};
  categories
    .filter((c) => c.parent === parent)
    .forEach((c) => (node[c.id] = makeTree(categories, c.id)));
  return node;
};

console.log(JSON.stringify(makeTree(categories, null), null, 2));
```

Output:

```javascript
{
  "animals": {
    "mammals": {
      "cats": {
        "persian": {},
        "siamese": {}
      },
      "dogs": {
        "chihuahua": {},
        "labrador": {}
      }
    }
  }
}
```

## Explanation for Example 2:

- The `make` tree function takes an array of cateogires and a parent caegory as input. It returns a tree-like structure that represents the hierarchy of categories. The tree structure is represented as a nested object where each node in the object represents a category, and its properties represent its subcategories.
- The function starts by creating an empty object `node` that will eventually represent the current category.
- THe function uses the `filter` method to filter the `cateogires` array and return only those cateogiores whose `parent` property matches the `parent` argument passed to the function.
- For each of the filtered categories, the function adds a porperty to the `node` object with the same name as the `id` property of the category, and sets the value of that property to the result of calling `makeTree` again with the `categories` array and the `id` of the current category as the new `parent` argument.
- This process repeats recursively, building up the tree-like strucutre as the function calls itself for each subcategory. When there are no more categories, with the current `parent`, the function returns the `node` object, representing the complete hierarchy of categories for the current parent.
- Last, the `console.log();` statement outputs the resulting tree using `JSON.stringify`m the second argument in `JSON.stringify` specifies the number of spaces to use for indentation, which is set to `2` to make the output easier to read.
