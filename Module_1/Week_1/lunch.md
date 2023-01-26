## Challenge

- If we're not hungry, we want to tell ourselves to get back to work.
- Otherwise, we want to pick something up and eat it in the lab when we've got less than 20 minutes or to try a place nearby if we've got between 20 and 30 minutes. If we have any more time than that we want to remind ourselves that we're in a bootcamp and that we should reconsider how much time we actually have to spare.
- `hungry` is a Boolean, representing if you're hungry or not.
- `availableTime` is a Number representing the time you have for lunch, in minutes.

## Solution

```javascript
const whatToDoForLunch = function (hungry, availableTime) {
  if (hungry === false && availableTime) {
    return "Get back to work";
  } else if (hungry === true && availableTime < 20) {
    return "Picking something up and eat it in the lab";
  } else if (hungry === true && availableTime >= 20 && availableTime <= 30) {
    return "Try a place nearby";
  } else {
    return "We are in bootcamp, reconsider how much time you have to spare";
  }
};
```

## Explanation

This function is called `whatToDoForLunch` and it takes two parameters: `hungry` and `availableTime`. It uses an if-else statement to determine what to do for lunch based on the values of the two parameters.

- If the "hungry" parameter is "false" and "availableTime" is truthy (i.e. not undefined, null, 0, false, NaN, or an empty string), the function returns the string "Get back to work".

- If the "hungry" parameter is "true" and "availableTime" is less than 20, the function returns the string "Picking something up and eat it in the lab".

- If the "hungry" parameter is "true" and "availableTime" is greater than or equal to 20 and less than or equal to 30, the function returns the string "Try a place nearby".

- If none of the above conditions are met, the function returns the string "We are in bootcamp, reconsider how much time you have to spare".
