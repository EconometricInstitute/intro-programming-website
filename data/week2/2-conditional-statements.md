---
path: '/week-2/2-conditional-statements'
title: 'Conditional Statements'
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

- Become familiar with the idea of a conditional statement and learn how to create a program containing optional operations through the use of conditional statements.

- Become familiar with comparison and logical operators commonly used in conditional statements.

- Learn how to compare both numbers and strings by remembering the equals-command for strings.

- Become familiar with the order of execution for a conditional statement, and know that the parsing of a conditional statement stops at the first condition whose statement evaluates to true.

</text-box>

So far, our programs have followed a straightforward execution from top to bottom, without incorporating any conditions or conditional behavior. However, in most cases, we need to include conditional logic in our programs. This logic is dependent on the state of the program's variables.

To introduce conditional branching in a program based on user input, we need to use what is known as a **conditional statement**. The most basic form of a conditional statement is as follows.

```java
System.out.println("Hello, world!");
if (true) {
    System.out.println("This code is unavoidable!");
}
```

<sample-output>

Hello, world!
This code is unavoidable!

</sample-output>

Conditional statements are used to make decisions based on the state of the program's variables. In Java, the most basic conditional statement is the `if` statement. It begins with the keyword `if`, followed by parentheses that contain an expression to be evaluated.

The expression inside the parentheses is evaluated when the conditional statement is reached. The result of the evaluation is a boolean value. If the expression evaluates to `true`, the source code inside the block that follows the conditional statement is executed. On the other hand, if the expression evaluates to `false`, the execution skips the source code inside the block and moves on to the statement after the closing curly bracket of the current conditional statement.

It's important to note that an `if` statement is not followed by a semicolon because the statement doesn't end after the conditional. Instead, the curly braces `{}` are used to define the block of code to be executed when the condition is `true`.

Here's an example that compares two numbers in a conditional statement:

```java
int number = 11;
if (number < 10) {
    System.out.println("The number was less than 10");
}
```
In this example, the variable `number` is assigned a value of `11`. The condition inside the parentheses, `number < 10`, evaluates to `false`. Therefore, the source code inside the block that follows the conditional statement is not executed and the sentence "The number was less than 10" will not be printed.

<programming-exercise name="Speeding Ticket">

Write a program that asks the user for an integer and prints the string "Speeding ticket!" if the input is (strictly) greater than 120.

<sample-output>

Give speed:
**15**

</sample-output>

<sample-output>

Give speed:
**135**
Speeding ticket!

</sample-output>

</programming-exercise>

## Code Indentation and Block Statements
A code block is a section of code enclosed by a pair of curly brackets. In Java, the source file containing a program must include the string `public class`, followed by the name of the program and the opening curly bracket of the block. The block ends with a closing curly bracket. The recurring snippet `public static void main(String[] args)` begins a block, and the source code within it is executed when the program is run. This snippet is the starting point of all Java programs. Blocks define a program's structure and its boundaries. It's important to note that a curly bracket must always have a matching pair: any code missing a closing (or opening) curly bracket is invalid.

A conditional statement also marks the start of a new code block. In addition to defining program structure and functionality, block statements have an effect on the readability of a program. Code inside a block is typically indented for clarity. For example, any source code inside the block of a conditional statement is indented four spaces deeper than the `if` command that started the conditional statement. Four spaces can also be added by pressing the `tab` key. When the block ends with a `}` character, the indentation also ends. The `}` character should be at the same level of indentation as the `if` command that started the conditional statement.

The example below shows correct indentation:

```java
if (number > 10) {
    number = 9;
}
```

In Java, code should be indented consistently with either four spaces or a single tab for each block. It's important to use only one of these methods for indentation, not both. To automatically indent code in IntelliJ, use the shortcut `Ctrl + alt + L`. From now on, it's important to indent code correctly in exercises and graded assignments, as incorrect indentation may result in lost style points.

## Relational Operators
As you may have noticed, conditional statements often use comparison operators, also known as `relational operators`, to compare numbers. Java provides a set of standard relational operators for this purpose:

- `>` greater than
- `>=` greater than or equal to
- `<` less than
- `<=` less than or equal to
- `==` equal to
- `!=` not equal to

An example of two relational operators being used in code is given below:
```java
int number = 55;

if (number != 0) {
    System.out.println("The number is not equal to 0");
}

if (number >= 1000) {
    System.out.println("The number is at least 1000");
}
```

<programming-exercise name="Orwell">

Write a program that prompts the user for an integer and prints the string "Orwell" if the number is exactly 1984.

<sample-output>

Give a number:
**1983**

</sample-output>

<sample-output>

Give a number:
**1984**
Orwell

</sample-output>

</programming-exercise>

## Else
If the expression inside the parentheses of the conditional statement evaluates to false, then the execution of the code moves to the statement following the closing curly bracket of the current conditional statement. This is not always desirable, and usually, we want to provide an alternative option when the conditional expression evaluates to false. This can be achieved using the `else` command, which is used together with the `if` command.

```java
int number = 4;

if (number > 5) {
    System.out.println("Your number is greater than five!");
} else {
    System.out.println("Your number is five or less!");
}
```

If an `else` branch has been specified for a conditional statement, the block defined by the `else` branch is executed when the condition of the conditional statement is false. The `else` command is placed on the same line as the closing bracket of the block defined by the `if` command. In the example stated above, the argument for the if-statement is false, so the program will execute the block under the `else` command. The output will be: "Your number is five or less."

<programming-exercise name="Adulthood">

Write a program that prompts the user for their age and tells them whether they are an adult (18 years old or older).

<sample-output>

How old are you?
**12**
You are not an adult

</sample-output>

<sample-output>

How old are you?
**32**
You are an adult

</sample-output>

</programming-exercise>

## More Conditionals: else if
In cases where there are multiple conditions to be evaluated, we use the `else if` command. This command is placed after the initial `if` condition and can be used multiple times.

```java
int number = 3;

if (number == 1) {
    System.out.println("The number is one");
} else if (number == 2) {
    System.out.println("The given number is two");
} else if (number == 3) {
    System.out.println("The number must be three!");
} else {
    System.out.println("Something else!");
}
```

Let's read out the example above: 'If the number is one, then print "The number is one", else if the number is two, then print "The given number is two", else if the number is three, then print "The number must be three!". Otherwise, print "Something else!"'

The step-by-step visualization of the code above is as follows:

<code-states-visualizer input='{"code":"public class Example {\n  public static void main(String[] args) {\n    int number = 3;\n    \n    if (number == 1) {\n      System.out.println(\"The number is one\");\n    } else if (number == 2) {\n      System.out.println(\"The given number is two\");\n    } else if (number == 3) {\n      System.out.println(\"The number must be three!\");\n    } else {\n      System.out.println(\"Something else!\");\n    }\n  }\n}","stdin":"","trace":[{"stdout":"","event":"call","line":3,"stack_to_render":[{"func_name":"main:3","encoded_locals":{},"ordered_varnames":[],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"1","frame_id":1}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":3,"stack_to_render":[{"func_name":"main:3","encoded_locals":{},"ordered_varnames":[],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"2","frame_id":2}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":5,"stack_to_render":[{"func_name":"main:5","encoded_locals":{"number":3},"ordered_varnames":["number"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"4","frame_id":4}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":7,"stack_to_render":[{"func_name":"main:7","encoded_locals":{"number":3},"ordered_varnames":["number"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"8","frame_id":8}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":9,"stack_to_render":[{"func_name":"main:9","encoded_locals":{"number":3},"ordered_varnames":["number"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"12","frame_id":12}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":10,"stack_to_render":[{"func_name":"main:10","encoded_locals":{"number":3},"ordered_varnames":["number"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"16","frame_id":16}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"The number must be three!\n","event":"step_line","line":14,"stack_to_render":[{"func_name":"main:14","encoded_locals":{"number":3},"ordered_varnames":["number"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"20","frame_id":20}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"The number must be three!\n","event":"return","line":14,"stack_to_render":[{"func_name":"main:14","encoded_locals":{"number":3,"__return__":["VOID"]},"ordered_varnames":["number","__return__"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"21","frame_id":21}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}}],"userlog":"Debugger VM maxMemory: 455M\n"}'></code-states-visualizer>

<programming-exercise name="Larger Than or Equal To">

Write a program that prompts the user for two integers and prints the larger of the two. If the numbers are the same, then the program informs us about this as well.

Sample outputs:

<sample-output>

Give the first number:
**5**
Give the second number:
**3**
Greater number is: 5

</sample-output>

<sample-output>

Give the first number:
**5**
Give the second number:
**8**
Greater number is: 8

</sample-output>

<sample-output>

Give the first number; **5**
Give the second number: **5**
The numbers are equal!

</sample-output>

</programming-exercise>

In the following video, we show what it looks like when we write a program using if, else and if-else systems in IntelliJ.

<panopto src="https://eur.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=72ad852b-4f50-4e72-bdac-ace200f7437c&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all"></panopto>


## Conditional Statement Expression and the Boolean Variable
The expression inside the parentheses of a conditional statement must evaluate to a boolean value, which can either be `true` or `false`. A conditional statement can also be constructed with a boolean variable, like so:

```java
boolean isItTrue = true;
if (isItTrue) {
    System.out.println("Pretty wild!");
}
```

Apart from being used in conditionals, comparison operators can also be used to produce boolean values that can be stored in boolean variables for later use. For example:

```java
int first = 1;
int second = 3;
boolean isGreater = first > second;
```

In the example above, the boolean variable `isGreater` now stores the boolean value `false`. We can further extend the previous example by adding a conditional statement:

```java
int first = 1;
int second = 3;
boolean isLessThan = first < second;

if (isLessThan) {
    System.out.println("1 is less than 3!");
}
```
The program will output: 1 is less than 3!

### Modulo operator
An operator which is very useful when we want to check the divisibility of a number is the modulo operator. The symbol for this modulo operator is `%` and the output of a modulo operator is the remainder after division of the first number by the second number.

```java
int remainder = 7 % 2;
System.out.println(remainder); // prints 1
System.out.println(5 % 3); // prints 2
System.out.println(7 % 4); // prints 3
System.out.println(8 % 4); // prints 0
System.out.println(1 % 2); // prints 1
```

For instance, if we would want to know whether a number given by the user is divisible by four hundred, we could check if the remainder is zero after taking the modulo of the number and four hundred. Since the modulo is an operation just like other calculations, it can be a part of an expression in a conditional statement.

```java
Scanner reader = new Scanner(System.in);

int number = Integer.valueOf(reader.nextLine());

if (number % 400 == 0) {
    System.out.println("The number " + number + " is divisible by four hundred.");
} else {
    System.out.println("The number " + number + " is not divisible by four hundred.");
}
```

## Conditional Statements and Comparing Strings
Although integers, floating-point numbers, and boolean values can be compared using two equals signs (`variable1 == variable2`), the same approach cannot be used for comparing the equality of strings.

You can try this with the following program:

```java
Scanner reader = new Scanner(System.in);

System.out.println("Enter the first string");
String first = reader.nextLine();
System.out.println("Enter the second string");
String second = reader.nextLine();

if (first == second) {
    System.out.println("The strings were the same!");
} else {
    System.out.println("The strings were different!");
}
```

<sample-output>

Enter the first string
**same**
Enter the second string
**same**
The strings were different!

</sample-output>

<sample-output>

Enter the first string
**same**
Enter the second string
**different**
The strings were different!

</sample-output>

This is due to how Java implements variable comparison and the internal workings of strings. Since strings can contain a limitless number of characters, and variables that contain only one number or value can be compared using an equals sign, using such method for strings doesn't work. We will explore this topic further in this course.

When comparing strings, it is important to use the `equals` command, which is specifically designed for string variables. This command is written after a string by appending it to the end of the string to be compared using a dot. It takes a parameter, which is the string to be compared against the variable. If the variable is being compared with a string directly, the string can be placed inside the parentheses of the `equals` command, enclosed in quotation marks. On the other hand, if a string variable holds the string to be compared, the name of the variable should be placed inside the parentheses. The `equals` command works as follows:

```java
Scanner reader = new Scanner(System.in);

System.out.println("Enter a string");
String input = reader.nextLine();

if (input.equals("a string")) {
    System.out.println("Great! You read the instructions correctly.");
} else {
    System.out.println("Missed the mark!");
}
```

In the example below the user is prompted for two strings. We first check to see if the provided strings are the same, after which we check if the value of either one of the two strings is "two strings".

```java
Scanner reader = new Scanner(System.in);

System.out.println("Input two strings");
String first = reader.nextLine();
String second = reader.nextLine();

if (first.equals(second)) {
    System.out.println("The strings were the same!");
} else {
    System.out.println("The strings were different!");
}

if (first.equals("two strings")) {
    System.out.println("Clever!");
}

if (second.equals("two strings")) {
    System.out.println("Sneaky!");
}
```
<programming-exercise name="Same">

Write a program that prompts the user for two strings. If the strings are the same, then the program prints "Same". Otherwise, it prints "Different".

<sample-output>

Enter the first string:
**hello**
Enter the second string:
**hello**
Same

</sample-output>

<sample-output>

Enter the first string:
**hello**
Enter the second string:
**world**
Different

</sample-output>

</programming-exercise>

## Logical Operators
A conditional statement can contain an expression consisting of multiple parts, which can be combined using logical operators such as the **and** operator `&&`, **or** operator `||`, and **not** operator `!`.

- An expression that is made up of two expressions combined using the and-operator is only true if both of the expressions being combined evaluate to true.
- An expression that is made up of two expressions combined using the or-operator is true if either one, or both, of the expressions being combined evaluate to true.
- It is important to note that logical operators do not change the boolean value from true to false or false to true. They only combine and evaluate expressions.

In the next example we combine two individual conditions using the and-operator (`&&`). The code is used to check if `number` is greater than or equal to 5 and less than or equal to 10. In other words, we check whether 7 is within the range of 5-10, which should give the output "It is!":

```java
System.out.println("Is the number within the range 5-10? ");
int number = 7;

if (number >= 5 && number <= 10) {
    System.out.println("It is! :)");
} else {
    System.out.println("It is not :(")
}
```

In the next example we provide two conditions using the or-operator (`||`): is the number less than zero or greater than 100? The condition is fulfilled if the number fulfills either one of the two conditions, which is true for the number 145 for instance:

```java
System.out.println("Is the number less than 0 or greater than 100");
int number = 145;

if (number < 0 || number > 100) {
    System.out.println("It is! :)");
} else {
    System.out.println("It is not :(");
}
```

In the next example we flip the result of the expression `number > 4` using the not-operator (`!`). The not-operator is written in such a way that the expression to be flipped is wrapped in parentheses, whilst the not-operator is placed before these parentheses.

```java
int number = 7;

if (!(number > 4)) {
    System.out.println("The number is not greater than 4.");
} else {
    System.out.println("The number is greater than 4.");
}
```

<programming-exercise name='Checking the age'>

Write a program that prompts the user to input their age and checks whether this age is feasible (at least 0 and at most 120). Only use a single `if`-command in your program.

<sample-output>

How old are you?
**10**
OK

</sample-output>

<sample-output>

How old are you?
**55**
OK

</sample-output>

<sample-output>

How old are you?
**-3**
Impossible!

</sample-output>

<sample-output>

How old are you?
**150**
Impossible!

</sample-output>

</programming-exercise>

## Execution order
#### Order of Execution for Comparisons
Comparisons are always executed top down. Whenever execution reaches a conditional statement whose condition is `true`, its block is executed and the comparison stops.

```java
int number = 5;

if (number == 0) {
    System.out.println("The number is zero.");
} else if (number > 0) {
    System.out.println("The number is greater than zero.");
} else if (number > 2) {
    System.out.println("The number is greater than two.");
} else {
    System.out.println("The number is less than zero.");
}
```

The example above prints the string "The number is greater than zero." even if the condition `number > 2` is true. The comparison namely stops at the first condition that evaluates
to true.

#### Execution Order of Conditional Statements
Let's familiarize ourselves with the execution order of conditional statements through a classic programming exercise.

_'Write a program that prompts the user for a number between one and one hundred, and prints that number. If the number is divisible by three, then print "Fizz" instead of the number. If the number is divisible by five, then print "Buzz" instead of the number. If the number is divisible by both three and five, then print "FizzBuzz" instead of the number.'_

The programmer begins to solve the exercise by reading the exercise description and by writing code according to the description. The conditions for execution are presented in a given order by the description, and the initial structure for the program is formed based on that order. The structure is formed based on the following steps:

- Write a program that prompts the user for a number and prints that number.

- If the number is divisible by three, then print "Fizz" instead of the number.

- If the number is divisible by five, then print "Buzz" instead of the number.

- If the number is divisible by both three and five, then print "FizzBuzz" instead of the number.

If-type conditions are easy to implement using `if` - `else if` - `else` -conditional statements. The code below was written based on the steps above, but it does not work correctly, which we can see from the example.

```java
Scanner reader = new Scanner(System.in);

int number = 15;

if (number % 3 == 0) {
    System.out.println("Fizz");
} else if (number % 5 == 0) {
    System.out.println("Buzz");
} else if (number % 3 == 0 && number % 5 == 0) {
    System.out.println("FizzBuzz");
} else {
    System.out.println(number);
}
```

The problem with the previous approach is that **the parsing of conditional statements stops at the first condition that is true**. E.g., with the value 15 the string "Fizz" is printed, since the number is divisible by three (15 % 3 == 0), whereas we would actually want to see "FizzBuzz".

One approach for improving and developing the correct train of thought would be to first find the **most demanding condition**, and implement it. After that, we would implement the other conditions. In the example above, the condition "if the number is divisible by both three **and** five" requires two things to happen. Now the train of thought would be:

1. Write a program that reads input from the user.

2. If the number is divisible by both three and five, then print "FizzBuzz" instead of the number.

3. If the number is divisible by three, then print "Fizz" instead of the number.

4. If the number is divisible by five, then print "Buzz" instead of the number.

5. Otherwise, the program prints the number given by the user.

This corresponds to the following code:

```java
Scanner reader = new Scanner(System.in);

int number = Integer.valueOf(reader.nextLine());

if (number % 3 == 0 && number % 5 == 0) {
    System.out.println("FizzBuzz");
} else if (number % 3 == 0) {
    System.out.println("Fizz");
} else if (number % 5 == 0) {
    System.out.println("Buzz");
} else {
    System.out.println(number);
}
```
