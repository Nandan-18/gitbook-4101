# Queen Industries

## Summary

We've tackled quite a few problem sets. It's time to shake things up a bit. I've provided a simple `Company` class, which demonstrates how simple organizational operations might take place \(e.g., hiring and firing employees, adjusting salaries, among other things\). Your job is to implement the missing classes and methods. You cannot change any of the methods and fields provided in the `Company` class, but you are free to add additional methods or fields as you see fit.

## Requirements

1. Create a repository called `queen-industries`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Pull down [the skeleton repository](https://github.com/ucvts/queen-industries-4101) containing starter code.
4. Implementing the missing classes and methods, making appropriate use of inheritance, polymorphism, and interfaces where applicable.
5. Add, commit, and push your code to your `queen-industries` repository.

## Analyzing the Starter Code

The only starter code you're getting is the `Company` class, as well as all-but-empty `Employee`, `Manager`, and `Director` classes. These are designed to simulate how employees, managers, and directors might interact in a fictitious company.

If you read carefully, you'll come across references and methods that aren't defined in any of the classes. Even if you don't read carefully, they should be glaringly obvious because the code won't compile with all of these unknown references.

Your job job is the implement the missing classes and methods so that the program compiles and runs as expected. You are writing your code to fit my specifications, which means you cannot modify the existing code, though you can \(and will have to!\) add to them.

## Entities

We're working with three types of staff members here: `Employee`, `Manager`, and `Director`. This is an organizational hierarchy, where a director supervises zero or more managers, and a manager supervises zero or more employees.

### Characteristics

A staff member, regardless of whether he or she is a director, manager, or employee, is defined by the follow characteristics.

* `Tier` \(employee = 1, manager = 2, director = 3\)
* `Salary`
* `Name`
* `Department`
* `Title`

Managers and directors are further defined by a bonus, as well as a list of direct reports.

* `Bonus`
* `Reports` \(each of whom must below the managerial or directorship tier, respectively\)

Additionally, directors are entitled to stock options

* `Stock Shares`

### Functionality

Employees can't really do much except offer up their own characteristic data. Managers and directors, though, have a bit more freedom.

#### Managers

A manager can hire and fire an employee, so long as the following conditions are met.

* The employee in question must be a direct report.
* The employee in question must be at a tier lower than that of the manager.

If one of these conditions is not met, your code must throw the appropriate exception.

```java
Exception in thread "main" java.lang.Exception: ERROR: cannot fire an Employee who is not a direct or indirect report.
	at Manager.fire(Manager1.java:66)
	at Company.testInvalidOperations(Company.java:264)
	at Company.main(Company.java:310)

Exception in thread "main" java.lang.Exception: ERROR: cannot fire an Employee of an equal or greater tier.
	at Manager.fire(Manager.java:64)
	at Company.testInvalidOperations(Company.java:272)
	at Company.main(Company.java:310)

Exception in thread "main" java.lang.Exception: ERROR: cannot hire an Employee of an equal or greater tier.
	at Manager.hire(Manager.java:53)
	at Company.testInvalidOperations(Company.java:279)
	at Company.main(Company.java:310)
```

Similar to hiring and firing, direct reports must adhere to the following constraint.

* All reports must be at a tier lower than that of the person to whom they report.

If this condition is not met, your code must throw the appropriate exception.

```java
Exception in thread "main" java.lang.Exception: ERROR: cannot supervise an Employee of an equal or greater tier.
	at Manager.validateReports(Manager.java:89)
	at Manager.<init>(Manager.java:13)
	at Director.<init>(Director.java:12)
	at Company.testInvalidOperations(Company.java:285)
	at Company.main(Company.java:310)
```

#### Directors

A director can hire and fire an employee or a manager, so long as the following conditions are met.

* The employee or manager in question must be a direct report.
* The employee or manager in question must be at a tier lower than that of the director.

If one of these conditions is not met, your code must throw the appropriate exception.

```java
Exception in thread "main" java.lang.Exception: ERROR: cannot fire an Employee who is not a direct or indirect report.
	at Manager.fire(Manager1.java:66)
	at Company.testInvalidOperations(Company.java:264)
	at Company.main(Company.java:310)

Exception in thread "main" java.lang.Exception: ERROR: cannot fire an Employee of an equal or greater tier.
	at Manager.fire(Manager.java:64)
	at Company.testInvalidOperations(Company.java:272)
	at Company.main(Company.java:310)

Exception in thread "main" java.lang.Exception: ERROR: cannot hire an Employee of an equal or greater tier.
	at Manager.hire(Manager.java:53)
	at Company.testInvalidOperations(Company.java:279)
	at Company.main(Company.java:310)
```

Similar to hiring and firing, direct reports must adhere to the following constraint.

* All reports must be at a tier lower than that of the person to whom they report.

If this condition is not met, your code must throw the appropriate exception.

```java
Exception in thread "main" java.lang.Exception: ERROR: cannot supervise an Employee of an equal or greater tier.
	at Manager.validateReports(Manager.java:89)
	at Manager.<init>(Manager.java:13)
	at Director.<init>(Director.java:12)
	at Company.testInvalidOperations(Company.java:285)
	at Company.main(Company.java:310)
```

The stack traces will differ \(i.e., line numbers, call hierarchy\), but the messages need to match.

## Expected Output

When you compile and execute the main method in the Company class, your code should output the following text to the console.

```text
Queen Industries Organization Chart
 - Felicity Smoak, Director of Engineering
 - Laurel Lance, Director of Marketing
 - Oliver Queen, Director of Sales

LOG: new Employee hired (Sara Lance, Engineering, QA Manager)
LOG: new Employee hired (Curtis Holt, Engineering, Development Manager)
LOG: new Employee hired (Moira Queen, Engineering, QA Analyst III)
LOG: new Employee hired (Quentin Lance, Engineering, QA Analyst II)
LOG: new Employee hired (Slade Wilson, Engineering, QA Analyst I)
LOG: new Employee hired (Adrian Chase, Engineering, QA Analyst III)
LOG: new Employee hired (Rene Ramirez, Engineering, QA Analyst II)
LOG: new Employee hired (Dinah Drake, Engineering, QA Analyst I)
LOG: new Employee hired (Malcolm Merlyn, Marketing, Social Media Manager)
LOG: new Employee hired (Thea Queen, Marketing, Social Media Analyst III)
LOG: new Employee hired (Tommy Merlyn, Marketing, Social Media Analyst II)
LOG: new Employee hired (Roy Harper, Marketing, Social Media Analyst I)
LOG: new Employee hired (Ricardo Diaz, Sales, Inside Sales Manager)
LOG: new Employee hired (Mar Novu, Sales, Outside Sales Manager)
LOG: new Employee hired (Emilko Queen, Marketing, Inside Sales Reprsentative III)
LOG: new Employee hired (Mia Smoak, Marketing, Inside Sales Representative II)
LOG: new Employee hired (William Clayton, Marketing, Outside Sales Representative III)
LOG: new Employee hired (Connor Hawke, Marketing, Outside Sales Representative II)

Queen Industries Organization Chart
 - Felicity Smoak, Director of Engineering
    - Sara Lance, QA Manager
       - Moira Queen, QA Analyst III
       - Quentin Lance, QA Analyst II
       - Slade Wilson, QA Analyst I
    - Curtis Holt, Development Manager
       - Adrian Chase, QA Analyst III
       - Rene Ramirez, QA Analyst II
       - Dinah Drake, QA Analyst I
 - Laurel Lance, Director of Marketing
    - Malcolm Merlyn, Social Media Manager
       - Thea Queen, Social Media Analyst III
       - Tommy Merlyn, Social Media Analyst II
       - Roy Harper, Social Media Analyst I
 - Oliver Queen, Director of Sales
    - Ricardo Diaz, Inside Sales Manager
       - Emilko Queen, Inside Sales Reprsentative III
       - Mia Smoak, Inside Sales Representative II
    - Mar Novu, Outside Sales Manager
       - William Clayton, Outside Sales Representative III
       - Connor Hawke, Outside Sales Representative II

LOG: existing Employee fired (Mar Novu, Sales, Outside Sales Manager)
LOG: reports re-assigned [William Clayton, Marketing, Outside Sales Representative III, Connor Hawke, Marketing, Outside Sales Representative II]
LOG: existing Employee fired (Roy Harper, Marketing, Social Media Analyst I)

Queen Industries Organization Chart
 - Felicity Smoak, Director of Engineering
    - Sara Lance, QA Manager
       - Moira Queen, QA Analyst III
       - Quentin Lance, QA Analyst II
       - Slade Wilson, QA Analyst I
    - Curtis Holt, Development Manager
       - Adrian Chase, QA Analyst III
       - Rene Ramirez, QA Analyst II
       - Dinah Drake, QA Analyst I
 - Laurel Lance, Director of Marketing
    - Malcolm Merlyn, Social Media Manager
       - Thea Queen, Social Media Analyst III
       - Tommy Merlyn, Social Media Analyst II
 - Oliver Queen, Director of Sales
    - Ricardo Diaz, Inside Sales Manager
       - Emilko Queen, Inside Sales Reprsentative III
       - Mia Smoak, Inside Sales Representative II
    - William Clayton, Outside Sales Representative III
    - Connor Hawke, Outside Sales Representative II

Employee     : Emilko Queen
Department   : Marketing
Title        : Inside Sales Reprsentative III
Compensation : 105000.0

Employee     : Emilko Queen
Department   : Marketing
Title        : Inside Sales Reprsentative III
Compensation : 112500.0

Employee     : Mia Smoak
Department   : Marketing
Title        : Inside Sales Representative II
Compensation : 90000.0

Employee     : Mia Smoak
Department   : Marketing
Title        : Inside Sales Representative II
Compensation : 85000.0

Employee     : Ricardo Diaz
Department   : Sales
Title        : Inside Sales Manager
Compensation : 130000.0

Employee     : Ricardo Diaz
Department   : Sales
Title        : Inside Sales Manager
Compensation : 155000.0

ERROR: cannot fire an Employee who is not a direct or indirect report.
ERROR: cannot fire an Employee of an equal or greater tier.
ERROR: cannot hire an Employee of an equal or greater tier.
ERROR: cannot supervise an Employee of an equal or greater tier.
ERROR: cannot alter salary of an Employee who is not a report.
```

At this point in the year, this should go without saying...but I'll say it anyway. When I say your output should match mine, I mean it should match exactly!

## Grading Considerations

You'll be graded, of course, on whether or not your code output matches mine.

Notably, though, I'll also be grading the elegance and efficiency of the use of inheritance, polymorphism, and interfaces in your design and implementation.

## Deliverables

1. Submit your repository URL.

Your program output should match mine exactly, and should make effective and appropriate use of inheritance, polymorphism, and interfaces.

## Deadline

All submissions are due on Canvas by 11:59pm on Monday, March 29, 2021.

