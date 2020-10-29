# Problem Set 8

## Summary

Last time, we used built-in methods of the String class. For this problem set, our focus will be on implementing our own classes and methods. I've provided a simple `ATM` class, which demonstrates how a user might perform simple online banking actions. Your job is to implement the missing classes and methods. You cannot change `ATM` class in any way.

## Requirements

1. Create a repository called `pset-8`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Pull down [the skeleton repository](https://github.com/ucvts/pset-8-4101) containing starter code.
4. Implementing the missing classes and methods.
5. Add, commit, and push your code to your `pset-8` repository.

## Analyzing the Starter Code

The only starter code you're getting is the `ATM` class. It's designed to simulate someone using an ATM \(hopefully we've all got a rough understanding of how this works\).

If you read carefully, you'll come across references and methods that aren't defined in the ATM class. Even if you don't read carefully, they should be glaringly obvious because the code won't compile with all of these unknown references.

Your job job is the implement the missing classes and methods so that the ATM class compiles and runs as expected. You are writing your code to fit my specifications, which means you cannot modify the `ATM` class in any way whatsoever.

## Reading the Documentation

Anything you're unable to glean from analyzing the `ATM` class, you'll need to turn to the public documentation. These Javadocs should look familiar if you've ever poked around the Oracle documentation for built-in Java classes.

[Download this `.zip` folder](https://canvas.instructure.com/files/114106258/download?download_frd=1), extract it, and open up the HTML files using the browser of your choosing.

## Extra Credit

Build a command line interface that actually allows users to login to their account, perform transactions, and logout. It doesn't have to be fancy, but should have the minimum features. This will be worth an extra 25 points on top of the already 75-point assignment.

### Login

Prompt the user to enter an account number. You already have two existing accounts, but feel free to populate the pseudo-database with more. This menu should constantly prompt \(and re-prompt\) the user until a valid account number is received.

```text
Account No.: 
```

### Menu

After successfully logging in, users should be presented with a simple menu. It should re-prompt the user if an option other than those presented is selected.

```text
[1] Deposit
[2] Withdraw
[3] Transfer
[4] Quit

::: 
```

#### Deposit

If the user selects the deposit option, they'll need to specify how much money.

```text
Amount to deposit: 100.25
```

This should accept only positive numeric values, of course.

#### Withdraw

If the user selects the withdraw option, they'll need to specify how much money.

```text
Amount to withdraw: 250.50
```

Again, this should only accept positive numeric values, and the user will need to have enough money to support the transaction.

#### Transfer

If the user selects the transfer option, they'll need to specify how much money, as well as the destination account number.

```text
Destination: 12345678
Amount to transfer: 500.75
```

The destination account number must exist, and the same rules should apply here as they do for both deposits and withdrawals.

## Deliverables

1. Submit your repository URL.

Your program output should match mine exactly for each of the exercises above. 

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, November 8, 2020.

