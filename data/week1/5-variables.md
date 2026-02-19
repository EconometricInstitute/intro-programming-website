---
path: '/week-1/5-variables'
title: 'Variables'
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

- Understand the concept of a variable. Know what variable types, names, and values are.

- Know how to create and use string, integer, floating-point, and boolean variables.

</text-box>

In the previous section, you learned about variables in the context of user input. Now, let's examine the common variable *types* used in Java. A variable can be thought of as a container that holds information of a specific type such as text (`String`), whole numbers (`int`), floating-point numbers (`double`), or whether something is true or false (`boolean`). To assign a value to a variable, use the equals sign (`=`).

```java
int months = 12;
```
The Java code `int months = 12;` above assigns the value 12 to an integer variable named `months`. This statement can be read as "the variable months is assigned the value 12". To print the variable's value along with a string, the addition operator (`+`) can be used, as can be seen in the examples below.

```java
String text = "contains text";
int wholeNumber = 123;
double floatingPoint = 3.141592653;
boolean trueOrFalse = true;

System.out.println("Text variable: " + text);
System.out.println("Integer variable: " + wholeNumber);
System.out.println("Floating-point variable: " + floatingPoint);
System.out.println("Boolean: " + trueOrFalse);
```
Output:

<sample-output>

Text variable: contains text
Integer variable: 123
Floating-point variable: 3.141592653
Boolean: true

</sample-output>

It is important to note that when printing variables, you do not need to use quotation marks. If you do, the name of the variable, such as `text` in `System.out.println("text");`, will be printed instead of its value. To correctly print the value of a variable, simply use the variable without quotation marks, for example `System.out.println(text);`.

<programming-exercise name="Recipe">

The template for this assignment already contains code to print a recipe consisting of milk and flour. In the print statements, two variables are used: an `int` variable named `gramsOfMilk` and a `double` variable `kilosOfFlour`. The first variable indicates the amount of milk, in grams, while the second indicates the amount of flour, in kilos.

Complete the assignment by declaring both variables with the correct amount, such that the following output is printed:

<sample-output>

This recipe requires the following ingredients
Grams of milk: 750
Kilos of flour: 1.5

</sample-output>

</programming-exercise>

Variable names are unique in Java, and therefore no two variables can have the same name. A variable is created when it is declared for the first time. If you try to declare a variable with the same name a second time, your compiler will give an error. The following program would thus lead to an error, as the variable pi is declared twice:

```java
public class Example {
    public static void main(String[] args) {
        double pi = 3.14;
        double pi = 3.141592653;

        System.out.println("The value of pi is: " + pi);
    }
}
```

## Changing a Value Assigned to a Variable
A variable is created at the time of its declaration and holds its initial value until a new value is assigned to it. To change the value of a variable, use a statement that includes the variable name, an equals sign, and the new value. The type of the variable does not need to be declared again as it has already been specified when the variable was first declared.

```java
int number = 123;
System.out.println("The value of the variable is " + number);

number = 42;
System.out.println("The value of the variable is " + number);
```
Output:

<sample-output>

The value of the variable is 123
The value of the variable is 42

</sample-output>

Let's look at the preceding program's execution step-by-step. When a variable appears in the program for the first time, one must tell the computer both its type (in this case `int`) and its name (in this case `number`). Then, the computer creates a 'named container' for the variable and the value on the right side of the equals sign is copied into this named container.

![](../img/drawings/part1.4-variable-change-1.png)

Whenever a variable is referenced by its name in a program, its value is retrieved from a container that has the corresponding name.

![](../img/drawings/part1.4-variable-change-2.png)

Whenever a value is assigned to an existing variable (here `number = 42`), the new value is copied in the place of the old value, and the old value disappears.

![](../img/drawings/part1.4-variable-change-3.png)

The variable is then referenced again by its name in the program. We proceed as normal, retrieving the value of `number` from a container having its name.

![](../img/drawings/part1.4-variable-change-4.png)

At the end of the program, you'll notice that the original value of the variable has vanished. A variable can hold only one value at a time.

## Variable's Type Persists
It is important to note that once the type of a variable has been declared, it cannot be changed. There are strict type compatibility rules in Java that prevent a value of one type from being assigned to a variable of a different type. For instance, a boolean value cannot be assigned to an integer variable and vice versa. However, there are exceptions such as assigning an integer to a double variable, as Java can automatically convert integers to doubles. On the other hand, a floating-point value cannot be assigned to an integer variable as this can result in a loss of information. These restrictions are in place to prevent programming errors and ensure data integrity.

```java
double floatingPoint = 0.42;
floatingPoint = 1; // Works

int value = 10;
value = floatingPoint; // Does not work
```

In Java, it is possible to convert a string containing an integer value to an integer variable by using the `Integer.valueOf(name)` method. This method takes a string argument, in this case `name`, which contains the value to be converted. The following example demonstrates how to convert a `string` "42" to an `int`. Note that it is important to make sure that the string contains an integer value before attempting the conversion.

```java
String valueAsString = "42";
int value = Integer.valueOf(valueAsString);
```

It is also possible to convert a string to a double or a boolean value. The methods used for these conversions are `Double.valueOf()` and `Boolean.valueOf()`, respectively. Both methods take a string argument, which contains the value to be converted. When converting a string to a boolean, the string must be "true" for the resulting boolean value to be `true`. The case sensitivity of the string is ignored, so both "true" and "TRUE" result in the boolean value of `true`. Any other string results in a boolean value of `false`.

## Naming Variables
Naming variables is a critical aspect of describing a program. It's essential to name your variables in a way that is easily understood by others. When approaching a problem, the developer decides on the terms used to describe the problem domain. The terminology, including variable names, must accurately describe the problem for anyone who may work with it in the future.

As you're defining the problem you're trying to solve, think about the concepts related to that problem and the appropriate terms that can describe them. If it's challenging to come up with relevant names, consider the terms that definitely don't describe the problem. Settle on some terminology that you'll use, and keep in mind that you can always improve it later.

Unfortunately, variable naming is limited by certain constraints. Names cannot contain certain special symbols, such as exclamation marks (!). Spaces are also not allowed, since they're used to separate parts of commands. The convention in Java is to use a style known as [camelCase](https://en.wikipedia.org/wiki/Camel_case "Camel case – Wikipedia"), which makes us write every word part with an uppercase letter. However, the first letter of a variable name is **always** lower-cased, for example: `int camelCaseVariable = 7;`

Numbers are allowed within a variable name as long as it does not start with a number. Also, the name cannot already be in use, including names of variables previously defined in the program or commands provided by Java. Diacritical letters, such as ä and ö, should not be used in variable names.

### Permissible Variable Names

* lastDayOfMonth = 20
* firstYear = 1952
* name = "Essi"

### Impermissible Variable Names

* last day of month = 20 (spaces are not allowed)
* 1day = 1952 (cannot start with number)
* beware! = 1910 (an exclamation mark cannot be included)
* 1920 = 1 (cannot start with number or consist of numbers solely)

## The Type of the Variable Informs of Possible Values
A variable's type determines the types of values that can be assigned to it. `String` types hold text, `int` types whole numbers, `double` floating-point numbers, and `boolean` types are either true or false. As such, the possible values of a given variable type are limited. For example, a string cannot contain an integer, nor can a double contain a boolean value.

| Type                                  | Example                 | Accepted values         |
| ------------------------------------- | ----------------------- | ----------------------- |
| Whole number, i.e., `int`             |  `int value = 4;`       | Values between -2147483648 and 2147483647.   |
| Floating-point number, i.e., `double` | `double value = 4.2;`   | Decimal numbers, with the greatest possible value being approximately 2<sup>1023</sup>.  |
| Text, i.e., `String`                  | `String text = "Hi!";`  | Text (enclosed in quotation marks).   |
| True or false value, i.e., `boolean`  | `boolean right = true;` | A boolean contains either the value `true` or `false`.   |

Note that when a decimal number is represented with a floating-point number, the value can be inaccurate as floating-points are incapable of representing all decimal numbers exactly.
