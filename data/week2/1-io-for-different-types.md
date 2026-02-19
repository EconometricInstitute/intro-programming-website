---
path: '/week-2/1-io-for-different-types'
title: 'Reading and Printing Variables of Different Type'
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

  - You learn to read inputs that are of different types

  - You learn how to print variables in a formatted way

</text-box>

Last week, we learned how to read user input for `String` and `int` data types using the `Scanner` class. To do so, we can utilize the following methods after declaring a `Scanner` with the variable name `scanner`:
``` java
  scanner.nextLine();
  scanner.nextInt();
```

In addition to `String` and `int`, the `Scanner` class provides handy methods for the other data types we covered last week, namely `boolean` and `double`. To read input for these data types, we can use the following methods:
``` java
  scanner.nextBoolean();
  scanner.nextDouble();
```

As an example, we can thus use the `Scanner` class to read all variable types that we have learned so far in the following way:
``` java
import java.util.Scanner;

public class Inputs {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Please enter some text");
        String message = scanner.nextLine();

        System.out.println("Please enter a boolean");
        boolean booleanValue = scanner.nextBoolean();

        System.out.println("Please enter an int");
        int intValue = scanner.nextInt();

        System.out.println("Please enter a double");
        double doubleValue = scanner.nextDouble();

        System.out.println("We were given the following input");
        System.out.println(message);
        System.out.println(booleanValue);
        System.out.println(intValue);
        System.out.println(doubleValue);

        scanner.close();
    }
}
```

It's important to note that the user must enter input of the correct type. If the input is not of the correct type, the `Scanner` tool will not be able to convert it to the correct variable type and an error will occur when the program is run. We will cover methods to handle such situations later in this course.

<programming-exercise name="Different Inputs">

In this assignment, you should write a program that reads three values: one corresponding to a `boolean` and two to a `double`. You should then print the value of the `boolean` and the sum of the two `double` inputs. The output of your program should look like this:

<sample-output>

Please enter a boolean:
**true**
Please enter the first double:
**9.2**
Please enter the second double:
**10.15**
The value of the boolean input: true
The sum of the double inputs: 19.35

</sample-output>

</programming-exercise>

## Converting Strings
When dealing with transferring a `String` value, obtained from user input, to a different type, there is another option available: using dedicated parsing methods. In this case, let us assume that we have a given `String` with the variable name `message`. We can then use the following methods to convert this `String` to the variable types we have seen so far:
``` Java
boolean booleanValue = Boolean.parseBoolean(message);
int intValue = Integer.parseInt(message);
double doubleValue = Double.parseDouble(message);
```

For example, converting the output of the `nextLine()` method of the `Scanner` class to an `int` value would then look as follows:
``` Java
import java.util.Scanner;

public class Conversion {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Please enter an int");
        int intValue = Integer.parseInt(scanner.nextLine());

        System.out.println("We were given the integer " + intValue);
    }
}
```

## Formatted Printing of Variables
In the first week, we learned to use the `System.out.println` method for printing `String` variables and variables of other types. For example, we learned that we could use the following code to print out the value of a `double` variable:
``` Java
public class DoublePrinting {
  public static void main(String[] args) {
    double pi = 3.141592653;

    System.out.println("The value is: " + pi);
  }
}
```

However, sometimes we want more control over what is exactly printed. For example, we might want to print only a few numbers behind the decimal point in the above example. This can be achieved by using the `System.out.printf()` command. To print the `double` variable in the above example to a precision of two digits behind the decimal point, we use the command:
``` Java
System.out.printf("The value is %.2f", pi);
```
Note that when using the method `System.out.printf`, we need to give it two arguments separated by a comma.
The first argument should be a `String` that represents what we want to print. In this `String`, we can use special flags to indicate where we want to insert the values of variables we're printing.
For example, the flag `%.2f` indicates that we want to print a double value with two decimal places. The `f` indicates that it's a floating point number, while the `.2` specifies the number of decimal places. To print the value of `pi` in this format, we place the flag `%.2f` in the `String` where we want to print `pi`.
The second argument we provide is the value that should replace the flag. In our example, we provide the value of `pi` as the second argument.

We can also use different flags to represent different variable types. Here are some examples:

- `%.xs` represents a `String`, where the number `x` specifies the maximum number of characters we want to print.
- `%.xf` represents a `double` value with a specified number of decimal places.
- `%.xe` represents a `double` value in scientific notation, where the number `x` specifies the number of decimal places.

Note that when we use `printf`, we're only changing the way the variable is displayed in the printed output. The actual variable remains unchanged.
Also, unlike `println`, `printf` does not start a new line after printing. If we want to start a new line, we would have to do this manually.

<programming-exercise name="Formatted Printing">

For this assignment, the sample code initializes a `double` variable `longNumber`. Your program should print this variable in two ways:
- With three digits behind the decimal point
- In scientific notation with two digits behind the decimal point

The output of your program should look like:
<sample-output>
With three digits: 12532.189
In scientific notation: 1.25e+04
</sample-output>

</programming-exercise>
