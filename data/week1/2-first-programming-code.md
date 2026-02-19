---
path: '/week-1/2-first-programming-code'
title: 'First Programming Code'
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

- Learn how to write and execute a simple program

- Become familiar with IntelliJ and testing your assignment code

</text-box>

In this lesson, you will write your first programming code in Java.
The goal is to write a program that prints the text `Hello World!` on execution.
We will guide you through the process step by step.

## Setting up for Coding
First, make sure that you have IntelliJ set-up.
When working on a campus computer, this should already be the case.
When working on your own computer, see [the installation instructions](/installation) for the necessary steps.

Next, download the code samples for this week from Canvas and open these in IntelliJ. The video below demonstrates you how to do this:

<panopto src="https://eur.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=6cc47a12-c757-49c0-a9db-ac26010c104f&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all"></panopto>

Note: an older version of IntelliJ is used in this video. If you are using the most recent version of IntelliJ, you can skip the steps from 0:15 to 0:32 in the video and follow these steps instead:
- Open the IntelliJ IDEA
- In the Welcome Screen, click on `Learn` in the menu on the left
- Click on `Enable Access` under the `Learn to Program` section
- Once it is finished, click on `Get Started`
- A new window pops up, in menu on the left go to `My Courses`
- At the bottom of the window, click on `Open course from disk`
- Select the **.zip file** that you downloaded and press `Ok`
- Click on `Start` in the new window that pops up
- IntelliJ may ask whether you trust the project. Click on `Trust Project`
- Select the `Hello World` task under the lesson `First Programming Code`

If you run into issues here, you can ask for help during the first week tutorial.

## Writing your first program
You are now ready to write your first program. In Java, programs require some mandatory code (known as boilerplate code) to indicate the program's name to the computer. Our program name is `HelloWorld` and has to correspond to the name of the file that contains the source code (i.e., `HelloWorld.java`).


```java
public class HelloWorld {
    public static void main(String[] args) {
        // Code comes here
    }
}
```

Program execution begins after the line `public static void main(String[] args) {` and concludes at the final `}`. Although the template may seem overwhelming, it will become a familiar concept throughout the course.
Note that, while our examples may not always display the template, it is actually required for every program file. As such, our examples might be a single line, such as example below illustrating the print command.

## Actual code
Let's write our first code between the curly brackets in the example! We will consider the statement:
``` Java
System.out.println("Hello World!");
```

Note that source code is read line-by-line, from left to right, with each statement ending with a semicolon (`;`).

The statement used in this program is specific to Java and outputs text to the console during program execution. The text to be printed is specified within the brackets, in this case `Hello World!`. Note that it's important to surround the printed text with quotation marks (`""`), which are not printed themselves.

When adding our code to the template again, our code looks like this:
``` Java
public class HelloWorld {
  public static void main(String[] args) {
      System.out.println("Hello World!");
  }
}
```

<programming-exercise name="Hello World">

The template for this assignment already contains the boilerplate that is needed for the assignment:
```java
public class HelloWorld {
    public static void main(String[] args) {
        // Code comes here
    }
}
```

Complete the code in such a way that it looks exactly like in the text above. Do so by replacing the comment `// Code comes here` by the printing statement in the text above. Your program should print the text `Hello World!` when executed.

You can check your code by clicking on the `Check` button that is shown in the bottom right of the screen.

</programming-exercise>

## Running the code
You are now ready to run your code! To run this program, click on the green triangle that has appeared in the margin and click on `run`. You can also use the keyboard shortcut `Ctrl + Shift + F10`. If you followed the above steps, you should now see that the text "Hello World!" is printed to the console, which you can read under the opened `Run` tab at the bottom of your screen. If you want to rerun your code, you can click on the green triangle in the top right corner, or use the keyboard shortcut `Shift + F10`.

<text-box variant="hint" name="Running code">

Even though running a program is straightforward, a complex process happens in the background. The Java compiler first converts the source code into Java bytecode. Then, the program is executed by a Java interpreter, executing the commands one by one.

This compile process influences error detection and feedback. The compiler can check for errors before the program is executed, and the IDE (Integrated Development Environment) provides immediate feedback on any issues.

The IDE makes the process easy by allowing the programmer to compile and execute the program with a single button press. It also continuously compiles the program, enabling it to report errors. For instance, changing the Hello World exercise print command to `System.out.println("Hello World!")`, by removing the semi-colon, will result in a line underlining and an error notification on the left side.

</text-box>
