---
path: '/week-1/3-printing'
title: "Printing"
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

- Learn to write a program that prints text.

- Learn what an "argument" is.
    
- Learn about code style and code comments.

</text-box>

In the previous lesson, we learned that using the command
```java
System.out.println("Hello World!");
```
results in the following output to be printed in the console:

<sample-output>

Hello World!

</sample-output>

The same command can be used to print other text as well. For example, to print `Goodbye!`, we would again use the `System.out.println` command, but now putting a different value between the brackets. This would look as follows:
``` Java
System.out.println("Goodbye!")
```
This leads to the below output being printed to the console.

<sample-output>

Goodbye!

</sample-output>

The text within the brackets of a function (in this case `System.out.println`) is referred to as an `argument`. Our first example used `"Hello World!"` as an argument, while the second used `"Goodbye!"`. But we can use any text, as long as it is enclosed in quotation marks `""`.

<programming-exercise name="Goodbye">

The template for this assignment already contains the boilerplate that is needed for the assignment:
```java
public class Goodbye {
    public static void main(String[] args) {
        // Code comes here
    }
}

```

Complete the assignment by replacing the comment `// Code comes here` by the necessary code. Your program should print the text below when it is run:

<sample-output>

Goodbye! I hope to see you again.

</sample-output>

You can check your code by clicking on the `Check` button that is shown in the bottom right of the screen.

</programming-exercise>


## Printing Multiple Lines

Programs are built by adding commands one by one, each on a new line. In the example, there are two instances of the `System.out.println` command, meaning that the program executes two print statements.

```java
public class Example {
    public static void main(String[] args) {
        System.out.println("Hello world!");
        System.out.println("... and the universe!");
    }
}
```

The program above will print:

<sample-output>

Hello world!
... and the universe!

</sample-output>


<text-box variant=hint name="Assignment guidelines">

 The format for printing in assignments is strictly specified. If a parenthesis is required, it must be included.
    This attention to detail is important in programming and missing a single character can result in an error. Common mistakes made by novice programmers include using a comma instead of a dot, writing `printin` instead of `println`, forgetting apostrophes, or leaving out semicolons.
    Each of these can cause an error and halt program execution. Learning programming involves making mistakes, and every error message presents an opportunity to learn. Stay vigilant for red error signs and take the time to understand them.   
       
</text-box>

<programming-exercise name="Multiple Lines">

The template for this assignment already contains the boilerplate that is needed for the assignment:
```java
public class MultipleLines {
    public static void main(String[] args) {
        // Code comes here
    }
}

```

Complete the assignment in such a way that your code prints the following output when run.

<sample-output>

Hello, this is your program!
My presence is only short-lived.
So I will now say Goodbye!

</sample-output>

</programming-exercise>

<text-box variant=hint name="Using a shortcut for printing">

Writing the command `System.out.println("...")` can be taxing. Try to write **sout** in IntelliJ on a blank line (within main) and press tab. Note how this will autocomplete to `System.out.println("...")`. This trick can be a time-saver in the future.

![](../img/soutVideo.gif)

</text-box>

## Code style and Code Comments

### Semicolon Separates Commands
Commands are separated with a semicolon `;`. We could, if we wanted to, write almost everything on a single line. However, it's not recommended as it makes the code difficult to understand.

```java
System.out.println("Hello "); System.out.println("world"); System.out.println("!");
```

<sample-output>

Hello
world
!

</sample-output>

Although the previous example works, it's important to consider readability for other programmers (and your future self!). Using line breaks makes the code easier to read as each line is focused on a single task. This makes it clear what each line is doing.

### Comments
Source code can be commented for clarity or to add notes. There are two types of comments:

- Single-line comments are marked with two slashes `//`. Everything following them on the same line is interpreted as a comment.

- Multi-line comments are marked with a slash and an asterisk `/*`, and closed with an asterisk followed by a slash `*/`. Everything between them is interpreted as a comment.

Below is an example of a program where both are used.

```java
public class Comments {
    public static void main(String[] args) {
        // Printing
        System.out.println("Text to print");
        System.out.println("More text to print!");
        /* Next:
        - more on printing
        - more practice
        - variables
        - ...
        */
        System.out.println("Some other text to print");
        // System.out.println("Trying stuff out")
    }
}
```

The example's last line highlights a useful case for comments. Code can be commented out instead of being deleted when testing something new. However, it's important to keep the code organized and avoid having old code in comments in the final version of the program.
