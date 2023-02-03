## Challenge

- Given the following data, implement a function calculateSalesTax that calculates the total sales and total tax, grouped by company.

```javascript
const salesTaxRates = {
  AB: 0.05,
  BC: 0.12,
  SK: 0.1,
};

const companySalesData = [
  {
    name: "Telus",
    province: "BC",
    sales: [100, 200, 400],
  },
  {
    name: "Bombardier",
    province: "AB",
    sales: [80, 20, 10, 100, 90, 500],
  },
  {
    name: "Telus",
    province: "SK",
    sales: [500, 100],
  },
];
```

- **Expected Results:**

```javascript
{
  Telus: {
    totalSales: 1300,
    totalTaxes: 144,
  },
  Bombardier: {
    totalSales: 800,
    totalTaxes: 40
  }
}
```

## Solution

```javascript
const calculateSalesTax = function (salesData, taxRates) {
  const results = {};

  for (const company of salesData) {
    const companyName = company.name;
    const companyProvince = company.province;
    let companyTotalSales = 0;
    for (const sale of company.sales) {
      companyTotalSales += sale;
    }
    const companyTaxRate = taxRates[companyProvince];
    const companyTotalTax = companyTotalSales * companyTaxRate;

    if (results[companyName]) {
      results[companyName].totalSales += companyTotalSales;
      results[companyName].totalTaxes += companyTotalTax;
    } else {
      results[companyName] = {
        totalSales: companyTotalSales,
        totalTaxes: companyTotalTax,
      };
    }
  }
  return results;
};
```

## Explanation

- `calculateSalesTax` takes in two parameters: `salesData` and `taxRates`. `salesData` is an array of objects containing a company's name, province, and sales. `taxRates` is an object containing a provinces sales tax rates.
- We initialize an empty object called `results`
- We use a `for...of` loop iterating over the `salesData` array, and on each iteration `company` contains the current company's sales data.
- We declare variables to store the data of each `company`:
  - `companyName` = the value of `name` in the `company` object
  - `companyProvince` = the value of `province` in the `company` object.
  - `companyTotalSales` = `0`
  - To find the actual value of `companyTotalSales` we use a `for...of` loop iterating of the `sales` array in each `company` object.
- We declare more variables to store the tax rates and total amount of tax each company has paid:
  - `companyTaxRate` accesses the `taxRates` object with the the `companyProvince` property om the current `company` object in the loop from `salesData`.
  - `companyTotalTax` = `companyTotalSales` multiplied by `companyTaxRate`
- We check if the company name exists the `results` object
  - if it does we add the current company's `companyTotalsSales` and `companyTotalTax` to the exisiting values in the `results` object.
  - if the company name does not exist in the `results` object, we create a new object for that company and assign it's `totalSales` to `companyTotalsSales` and `totalTaxes` to `companyTotalTax`.
- After we finish the loop, we return the `results` object.
