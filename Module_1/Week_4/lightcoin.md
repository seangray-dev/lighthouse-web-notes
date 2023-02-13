## Challenge

Here's a list of features that our code needs to support:

- Allow multiple accounts to be created
- Each account can have many transactions
- Allow withdrawals and deposits into accounts
- Allow us to retrieve the transaction history of an account (all withdrawals and deposits)
- Allow us to retrieve the current balance of the account at any time
- Don't allow withdrawals that exceed the remaining balance of the account

## Solution

```javascript
class Account {
  constructor(username) {
    this.username = username;
    this.transactions = [];
  }

  get balance() {
    let balance = 0;
    for (const transaction of this.transactions) {
      balance += transaction.value;
    }
    return balance;
  }

  addTransaction(transaction) {
    this.transactions.push(transaction);
  }
}

class Transaction {
  constructor(amount, account) {
    this.amount = amount;
    this.account = account;
  }

  commit() {
    this.time = new Date();
    this.account.addTransaction(this);
  }
}

class Deposit extends Transaction {
  get value() {
    return this.amount;
  }

  isAllowed() {
    return true;
  }
}

class Withdrawal extends Transaction {
  get value() {
    return -this.amount;
  }

  isAllowed() {
    return this.account.balance - this.amount >= 0;
  }
}
```

## Explanation

An `Account` can have multiple `Transactions` associated with it.
The `Account` class has a `username` property, which is passed as an argument to the `constructor` and is used to create an instance of the class. It also has an array of `transactions` which holds all the transactions associated with the account, and a `balance` property which is computed as the sum of all transaction values. The `Account` class has 2 methods: `addTransaction` which adds a new transaction to the `transactions` array, and `get balance` which returns the current balance of the account.

The `Transaction` class has 2 properties: `amount` and `account`, and a mehtod `commit` which adds thr transaction to the `transactions` array of the associated account. The `commit` method also adds a `time` property to the transaction which is set to the current date and time.

The `Deposit` and `Withdraw` classes extend the `Transaction` class and are used to represent deposits and withdraws. The `Deposit` class has a `value` property which is equal to the `amount` property and `isAllowed` method which always returns `true`. The `Withdraw` class also has a `value` property which is equal to the negative of the `amount` property and `isAllowed` method which only returns `true` if the withdraw amount does not exceed the current account balance.
