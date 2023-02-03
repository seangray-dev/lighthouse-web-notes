# Challenges

- Here is a data structure representing a social network.

```javascript
const data = {
  f01: {
    name: "Alice",
    age: 15,
    follows: ["f02", "f03", "f04"],
  },
  f02: {
    name: "Bob",
    age: 20,
    follows: ["f05", "f06"],
  },
  f03: {
    name: "Charlie",
    age: 35,
    follows: ["f01", "f04", "f06"],
  },
  f04: {
    name: "Debbie",
    age: 40,
    follows: ["f01", "f02", "f03", "f05", "f06"],
  },
  f05: {
    name: "Elizabeth",
    age: 45,
    follows: ["f04"],
  },
  f06: {
    name: "Finn",
    age: 25,
    follows: ["f05"],
  },
};
```

- Implement solutions to the following questions/problems by writing functions for each one:

## Challenge 1

- Implement a function `biggestFollower()` which returns the name of the individual who follows the most people.

## Solution 1

```javascript
const biggestFollower = function (obj) {
  let result = "";
  let highestFollowCount = 0;

  for (const person in obj) {
    const followCount = obj[person].follows.length;
    if (followCount > highestFollowCount) {
      highestFollowCount = followCount;
      result = obj[person].name;
    }
  }

  return result;
};

console.log(biggestFollower(data)); // -> Debbie
```

## Explanation 1

- `biggestFollower` takes an `obj` as the input.
- We declare 2 variables: `result` as an empty string and `highestFollowCount` as `0`.
- We use a `for...in` loop iterating over the `obj` passed in, and `person` represents the key of each property in `obj`.
- We declare another variable named `followCount` which calculates the number of people person follows by using `obj[person].follows.length` for each `person`.
- We then check if the `followCount` is greater than `highestFollowCount`
  - if it is we update `highestFollowCount` to be `followCount`, and then update the `result` to the current `person`'s name using `obj[person].name`
- Lastly when the loop is finished we return the `result`

## Challenge 2

- Implement `mostPopular()` which returns the name of the most popular (most followed) individual.

## Solution 2

```javascript
const mostPopular = function (obj) {
  let count = {};
  let mostFollowedName = "";
  let mostFollowedCount = 0;

  for (const person in obj) {
    for (const follow of obj[person].follows) {
      count[follow] = (count[follow] || 0) + 1;
    }
  }

  for (const person in obj) {
    const name = obj[person].name;
    const followers = count[person] || 0;

    if (followers > mostFollowedCount) {
      mostFollowedCount = followers;
      mostFollowedName = name;
    }
  }

  return mostFollowedName;
};

console.log(mostPopular(data)); // -> Debbie
```

## Explanation 2

## Challenge 3

- Implement `printAll()` which outputs a list of everyone and for each of them, the names of who they follow and who follows them.

## Solution 3

```javascript
const printAll = function (obj) {
  let result = "";
  for (const person in obj) {
    const name = obj[person].name;
    const follows = [];
    const followers = [];
    for (const id of obj[person].follows) {
      follows.push(obj[id].name);
    }

    for (const followerId in obj) {
      if (obj[followerId].follows.includes(person)) {
        followers.push(obj[followerId].name);
      }
    }
    result += `${name} follows ${follows.join(
      ", "
    )} and is followed by ${followers.join(", ")}\n`;
  }
  return result;
};

console.log(printAll(data));
/* 
Alice follows Bob, Charlie, Debbie and is followed by Charlie, Debbie 

Bob follows Elizabeth, Finn and is followed by Alice, Debbie 

Charlie follows Alice, Debbie, Finn and is followed by Alice, Debbie 

Debbie follows Alice, Bob, Charlie, Elizabeth, Finn and is followed by Alice, Charlie, Elizabeth 

Elizabeth follows Debbie and is followed by Bob, Debbie, Finn 

Finn follows Elizabeth and is followed by Bob, Charlie, Debbie 
*/
```

## Explanation 3

## Challenge 4

- Implement `unrequitedFollowers()` which returns a list of names for those who follow someone that doesn't follow them back.

## Solution 4

```javascript
function unrequitedFollowers(obj) {
  const followsButNotFollwedBy = {};
  for (const person in obj) {
    const name = obj[person].name;
    for (const id of obj[person].follows) {
      if (!obj[id].follows.includes(person)) {
        if (!followsButNotFollwedBy[name]) {
          followsButNotFollwedBy[name] = [];
        }
        followsButNotFollwedBy[name].push(obj[id].name);
      }
    }
  }
  return followsButNotFollwedBy;
}

console.log(unrequitedFollowers(data));
```

## Explanation 4
