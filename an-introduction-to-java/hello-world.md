# Hello, World

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapter 3.1
{% endhint %}

## Your First Program

In nearly every language you learn, you'll start with the classic Hello, World! program. It's a simple program that prints a message to the console. Open up IntelliJ and follow along with this short video. In addition to walking you through creating and running your first program, it offers some cool tips and tricks when it comes to writing code in the IntelliJ IDE.

{% embed url="https://www.youtube.com/watch?v=H\_XxH66lm3U" %}

I recommend you choose a single folder where you'll keep all of your programming assignments for this course. Use this folder as your Project location for all IntelliJ projects.

## Code Review

I'm going to gloss over some of the finer details of how this program works for now. You'll have a much better understanding of the inner workings of the language soon enough. For now, let's focus on the broad strokes.

The very first line in file is something called a package statement.

* `package com.example.helloworld;`

For now, you can think of packages as folders. More complex programs often have many files \(usually called classes\), and packages are designed to organize these classes into logically related groups. They're not required, and the IDE will put everything in a default package if you omit the package statement.

Everything in Java lives inside of a class. You can think of classes as the outermost containers of program logic. On Line 3, you declared your class and gave it a name.

* `public class HelloWorld`

This line of code declares a new class called `HelloWorld`. You'll learn much more about classes later in the course. For now, you can think of classes as the outermost container of program logic. Everything in Java lives inside of a class, and every Java program consists of one or more classes.

This is one of those times where I'll be glossing over some details. `public` is a special keyword in Java \(called an access modifier\) that governs the accessibility of the class. `public` means the class is accessible from everywhere else in the program.

Lastly, `HelloWorld` is the name of the class. It's also the filename \(i.e., `HelloWorld.java`\). The filename must always match the class name, and this is case-sensitive.

On Line 4, you declared the `main` method.

* `public static void main(String[] args)`

A method is a collection of programming statements, and the `main` method is a special kind of method. Every Java application must have one, and it's where program execution begins.

The `public` access modifier means the same thing here as it did for the `HelloWorld` class. `static` and `void` are covered in detail later in the course. You need a little more background knowledge before an explanation of these two Java keywords will make any sense.

`main` is the name of the method. The JVM looks for this method in order to launch the program. `String[] args` is another expression that'll have to wait to be defined. For now, consider these class and method declarations as part of the plumbing required to create a Java application.

Inside of the main method, on Line 5, is the sole instruction we've written. It's called a print statement.

* `System.out.println("Hello, World!");`

This statement prints the text `Hello, World!` to the console when we execute the program.

## Syntax and Style

All languages have specific grammars, syntaxes, and vocabularies, and programming languages are no exception. You've already seen some of these elements in practice without even realizing it.

### Reserved Words

There are a set of reserved words that have a specific meaning in Java. You cannot use these words for anything other than their designed purpose.

* `class`
* `public`
* `static`
* `void`

Each of these words, among others, are reserved. For a complete list, see [Appendix A: Reserved Words](../helpful-resources/reserved-words.md).

### Indentation

Whitespace is ignored by the compiler, but that doesn't mean it's unimportant. Properly formatted code is easier to read, debug, and maintain. Indentation is an important part of formatting. Every time you nest one or more lines of code inside of a block, you must indent it.

The compiler won't care and your code will run all the same, but you will be graded on your style. I won't impose what style you choose \(there are many suitable choices\), but consistency will be expected.

### Common Mistakes

Programming languages are very particular, and you need to follow their syntax rules precisely. Java has some very specific rules. Your program will not compile if you don't follow them.

* Classes must be written in files of the same name.

If you have a class called `HelloWorld`, it must be written in a file called `HelloWorld.java`.

* Code blocks must be enclosed by curly braces.

A code block in Java is a container. Classes are blocks, and so are methods. Every opening curly brace must be aligned with a corresponding closing curly brace. One missing curly brace will break your entire program.

* Programming statements must end with a semicolon.

Your first program had only one statement: the `System.out.println` statement. And, as is required, this statement was terminated with a semicolon. Code blocks, such as classes and methods, are not statements. That's why they don't need semicolons.

* Java is case-sensitive.

Classes, methods, and Java keywords are all case-sensitive. Be sure you're using the appropriate case when writing your code. Java keywords are always written in lowercase letters, as is the `main` method.

### Conventions

There are a set of conventions that, while not strictly required by the compiler, are important to follow.

* Class names should be nouns written in mixed case.

Mixed case means the first letter is capitalized, along with each subsequent word in the class name. `HelloWorld` is a valid class name, but `helloworld` is not.

Naming conventions are one of many style conventions you'll be required to follow.

## Our First Repository

We're going to turn an existing project into a Git repository. And from there, we're going to push our changes up to GitHub. If that still sounds like gibberish, review the [Git and GitHub](git-and-github.md) section.

In the last section, we saw how to use Git from the command line and setup remote repositories on GitHub. You'll be expected to become comfortable working from the command line, but it's important to understand how to take advantage of features in the IntelliJ IDE.

Follow along with this short video that details the process of integrating Git and GitHub with your IDE. The IDE route is certainly faster and more convenient, but you need to understand what's going on under the hood. 

{% embed url="https://www.youtube.com/watch?v=mf2-MOl0VXY" %}

Alright, enough show-and-tell. Time to get our hands dirty!

{% page-ref page="../problem-sets/problem-set-0.md" %}

{% page-ref page="../problem-sets/problem-set-1.md" %}

