---
path: '/week-1/4-reading-input'
title: "Reading Input"
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

- Learn to write a program that reads user input.

- Learn how to concatenate text together.

</text-box>

Input refers to text written by a user and read by a program. To read input from a user, the `Scanner` tool from Java is used. This tool can be imported for use in a program by adding the command `import java.util.Scanner;` before the beginning of the main program's frame (`public class` ...). The tool itself is created with `Scanner scanner = new Scanner(System.in);`.

```java
import java.util.Scanner;

public class Program {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
    }
}
```

Below is an example of a program that prompts user input, reads the entered text, and prints it. The comments will guide you through the example for understanding. When finished with receiving input, one should close the scanner with the command `scanner.close();`. 

Close the scanner only after you're done getting input, with `scanner.close()`. But be cautious, as this also closes `System.in`, preventing the creation of a new scanner that uses `System.in`. Close it only when you're sure you won't use `System.in` again.

```java
// Introduce the scanner tool used for reading user input
import java.util.Scanner;

public class Program {
    public static void main(String[] args) {
        // Create a tool for reading user input and name it scanner
        Scanner scanner = new Scanner(System.in);

        // Print "Write a message: "
        System.out.println("Write a message: ");

        // Read the string written by the user, and assign it to program memory "String message = (string that was given as input)"
        String message = scanner.nextLine();

        // Close the scanner, because we received all input
        scanner.close();

        // Print the message written by the user
        System.out.println(message);
    }
}
```


Input is read using the `scanner` tool's `nextLine()` method. The `nextLine()` call waits for the user to enter text and press enter. The entered text is then assigned to the `String` variable `message`, where `String` is the variable type used in Java to store text. The program can reference the `message` variable later, for example to print it. When running the program, enter a message in the console as if you were the user. The `nextLine()` command reads the input and *returns* it as a `String`. To use the returned `String` in the program, it must be saved to a `String` variable (e.g. `String message = scanner.nextLine();`). A value saved in a variable can be reused.

<programming-exercise name='Message'>

Write a program that asks the user to input a string. When the user has provided a string (i.e., written some text and pressed the enter key), the program should print the string that was provided by the user.

The exercise template comes with a program template that includes the creation of a Scanner tool.

```java
import java.util.Scanner;

public class Message {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Write a message: ");
        // Write your program here
    }
}
```
Example output for when the user writes "Bye".

<sample-output>

Write a message:
**Bye**
Bye

</sample-output>

Example output for when the user writes "Once upon a time...".

<sample-output>

Write a message:
**Once upon a time...**
Once upon a time...

</sample-output>

</programming-exercise>

## Input String as a Part of Output
To integrate user input with other text as output, we use the addition (`+`) operator to join two pieces of text (`String`s) together. An example of this can be seen in the following program, that takes user input and combines it with another piece of text to print it as final output.


```java
import java.util.Scanner;

public class Program {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Write something: ");
        String message = scanner.nextLine();
        scanner.close();
        System.out.println("You wrote " + message);
    }
}
```
In examples of the output we indicate in bold what the user has entered in the scanner. When running the program, the following will happen:

Message in the console: `Write something:` will be printed

The user inputs `this` and presses enter.

The output will be: `You wrote this`

<programming-exercise name='Greeting'>

Write a program that prompts the user for their name with the message "What's your name?". When the user has written their name, the program has to print "Hi " followed by the user's name.

The exercise template already includes the code that creates the `Scanner` tool.

```java
import java.util.Scanner;

public class Greeting {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Write your program here
    }
}
```

Example output when user gives the name Ada.

<sample-output>

What's your name?
**Ada**
Hi Ada

</sample-output>

Example output when user gives the name Lily.

<sample-output>

What's your name?
**Lily**
Hi Lily

</sample-output>

</programming-exercise>

## Program Execution Waits for Input
When the program's execution reaches a statement that attempts to read input from the user (the command `reader.nextLine()`), the execution stops and waits. The execution continues only after the user has written some input and pressed enter.

In the example below, the program prompts the user for three strings. First, the program prints `Write the first string: `, and then waits for user input. Once the user has entered a string and pressed enter, the program prints the next prompt and waits for another string. This process repeats for three strings in total. After the program has received all three strings, it prints them. Note that if the scanner is done receiving input, the scanner should be closed.

```java
import java.util.Scanner;

public class Program {

    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);

        System.out.println("Write the first string:");
        String first = reader.nextLine();
        System.out.println("Write the second string:");
        String second = reader.nextLine();
        System.out.println("Write the third string:");
        String third = reader.nextLine();
        reader.close();

        System.out.println("Last string you wrote was " + third + ", which ");
        System.out.println("was preceded by " + second+ ".");
        System.out.println("The first string was " + first + ".");

        System.out.println("All together: " + first + second + third);
    }
}
```

<sample-output>

The output will look like this:
Write the first string:
**one**
Write the second string:
**two**
Write the third string:
**three**
Last string you wrote was three, which
was preceded by two.
The first string was one.
All together: onetwothree

</sample-output>
