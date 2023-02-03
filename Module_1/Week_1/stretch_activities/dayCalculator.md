## Challenge

- Read the code carefully and understand what it's trying to accomplish, then debug and fix any mistakes you find until you're confident it's producing the correct results.
- The tests below should equate to true

```javascript
console.log(calculateDayInYear("1900/3/2") === 61);
console.log(calculateDayInYear("2000/3/2") === 62);
console.log(calculateDayInYear("2012/2/29") === 60);
console.log(calculateDayInYear("2015/12/31") === 365);
```

## Solution

```javascript
function calculateDayInYear(date) {
  const splitDate = date.split("/");
  const year = Number(splitDate[0]);
  const month = Number(splitDate[1]);
  const day = Number(splitDate[2]);

  const validMonth = function (month) {
    return month && month >= 1 && month <= 12;
  };

  const validDay = function (month, day) {
    return day && day >= 1 && day <= DAYS_IN_MONTH[month - 1];
  };

  const calculateDayNumber = function (month, day) {
    let dayOfYear = day;

    for (let i = 1; i < month; i++) {
      dayOfYear += DAYS_IN_MONTH[i - 1];
    }

    return dayOfYear;
  };

  const daysInFeb = function (year) {
    return isLeapYear(year) ? 29 : 28;
  };

  const isLeapYear = function (year) {
    return (
      isMultiple(year, 400) || (!isMultiple(year, 100) && isMultiple(year, 4))
    );
  };

  const DAYS_IN_MONTH = [
    31,
    daysInFeb(year),
    31,
    30,
    31,
    30,
    31,
    31,
    30,
    31,
    30,
    31,
  ];

  if (year && validMonth(month) && validDay(month, day)) {
    console.log(
      date,
      "is day",
      calculateDayNumber(month, day),
      "of the year",
      year
    );
    return calculateDayNumber(month, day);
  } else {
    console.log("Invalid date");
  }
}

const isMultiple = function (numerator, denominator) {
  return numerator % denominator === 0;
};
```

## Explanation

- The `validMonth` function initally checked if `month` is greater than or equal to `1` & less than `12`, to fix this we need to check if `month` is greater than or equal to `1` & less or equal to `12`.

```javascript
const validMonth = function (month) {
  return month && month >= 1 && month < 12;
};

const validMonth = function (month) {
  return month && month >= 1 && month <= 12;
};
```

- `validDay` initially checked if `day` is greater than or equal to `1` and less than the number of days in the `month`, and needs to be fixed by checking if `day` is greater than or equal to `month`.

```javascript
const validDay = function (month, day) {
  return day && day >= 1 && day < DAYS_IN_MONTH[month - 1];
};

const validDay = function (month, day) {
  return day && day >= 1 && day <= DAYS_IN_MONTH[month - 1];
};
```

- In the `calculateDayNumber` we need to change `dayOfYear` starting at 1, to start at the value of `day` instead.

```javascript
const calculateDayNumber = function (month, day) {
  let dayOfYear = 1;

  for (let i = 1; i < month; i++) {
    dayOfYear += DAYS_IN_MONTH[i - 1];
  }

  return dayOfYear;
};

const calculateDayNumber = function (month, day) {
  let dayOfYear = day;

  for (let i = 1; i < month; i++) {
    dayOfYear += DAYS_IN_MONTH[i - 1];
  }

  return dayOfYear;
};
```

- `daysInFeb` always returned `28` and never utilized the function check for `isLeapYear`. Therefore we need to change this to returnining `29` if the `isLeapYear` is `true` and `28` otherwise.

```javascript
const daysInFeb = function (year) {
  return 28;
};

const daysInFeb = function (year) {
  return isLeapYear(year) ? 29 : 28;
};
```
