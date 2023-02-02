## Challenge

- Write code to filter the list down to only passing grades.
- This node script should print out passing grades to the console. Passing grades for this scenario can be those that are 70 or above.
- Tips:
  - Use the Array filter function (as shown previously) to print out only the passing grades.
  - Convert the anonymous function into an arrow function.

## Solution

```javascript
const grades = [73, 69, 3, 100, 50, 70, 69, 88, 95, 77, 35];

const passingGrade = grades.filter((grade) => grade >= 70);
```

## Explanation

- `filter` an array method creating a new array with all elements that pass it's callback function.
- `passingGrade` is a new array that only contains elements from the original `grades` array that are equal to or greater than 70.
- The callback function is `(grade) => grade >= 70` taking in an element (`grade`) and returning `true` of `false`.
- If `true`, the element is included in the `passingGrade` array, and if it's `false` it is not included in the new array.
