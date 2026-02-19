---
path: "/week-1/6-calculating"
title: "Calculating with Numbers"
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

- Learn to perform calculations with the help of variables.

- Know how to form printable statements including both calculations (expressions) and strings.

</text-box>

In Java, the basic mathematical operations include addition (`+`), subtraction (`-`), multiplication (`*`), and division (`/`). The order in which operations are performed follows the standard arithmetic rules: operations are performed from left to right, and expressions with `*` or `/` are calculated before expressions with `+` or `-`. This is consistent with the arithmetic principles taught in elementary school.

The following code demonstrates the assignment of values to two variables, first and second, and the calculation of their sum:

```java
int first = 2;
System.out.println(first); // prints 2
int second = 4;
System.out.println(second); // prints 4

int sum = first + second; // The sum of the values of the variables first and second is assigned to the variable sum
System.out.println(sum); // prints 6
```

## Precedence and Parentheses
The order of operations can be influenced by the use of parentheses. Operations within parentheses are executed first, before those outside of them. For example:

```java
int calculationWithParentheses = (1 + 1) + 3 * (2 + 5);
System.out.println(calculationWithParentheses); // prints 23

int calculationWithoutParentheses = 1 + 1 + 3 * 2 + 5;
System.out.println(calculationWithoutParentheses); // prints 13

```

The calculation process can also be divided into steps, as demonstrated below:

```java
int calculationWithParentheses = (1 + 1);
System.out.println(calculationWithParentheses); // prints 2
calculationWithParentheses = calculationWithParentheses + 3 * (2 + 5);
System.out.println(calculationWithParentheses); // prints 23

int calculationWithoutParentheses = 1 + 1;
calculationWithoutParentheses = calculationWithoutParentheses + 3 * 2;
calculationWithoutParentheses = calculationWithoutParentheses + 5;
System.out.println(calculationWithoutParentheses); // prints 13
```

<programming-exercise name="Seconds in a day">

In the given exercise template, you are tasked with creating a program that requests the user to input the number of days and calculates the equivalent number of seconds.

To read an integer input in Java, you can use the following code:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Give a number:");
int number = scanner.nextInt();
System.out.println("You gave " + number);
```

Here are some examples of the expected output:

<sample-output>

How many days would you like to convert to seconds?
**1**
86400

</sample-output>

<sample-output>

How many days would you like to convert to seconds?
**3**
259200

</sample-output>

<sample-output>

How many days would you like to convert to seconds?
**7**
604800

</sample-output>

</programming-exercise>

An *expression* is a combination of values that is turned into another value through a calculation or evaluation. Expressions are always evaluated before their values are assigned to a variable. Consider the following statement:

```java
int calculationWithoutParentheses = 1 + 1 + 3 * 2 + 5;
```
In this statement, the expression 1 + 1 + 3 * 2 + 5 is evaluated prior to its assignment to the variable calculationWithoutParentheses.

Evaluation of expressions takes place at the point in the program's source code where they are written. This means that expressions can be evaluated within a print statement, if they are used to calculate the value of the print statement's parameter. An expression does not change the value stored in a variable unless its result is either assigned to a variable or used as a parameter, for example, in printing.

```java
int first = 2;
int second = 4;

// this expression does not change the values of the variables, since its result is not assigned to any variable or used as a parameter in a print statement
first + second;
// In fact, it is not even allowed in Java
```

## Calculating and Printing
In Java, when one operand of the addition operator (+) is a string, the other operand will automatically be converted to a string as well during program execution. Consider the following example:

```java
System.out.println("Four: " + (2 + 2));
System.out.println("But! Twenty-two: " + 2 + 2);
```
The output of the program would be:

<sample-output>

Four: 4
But! Twenty-two: 22

</sample-output>

In the example, the integer `2` is turned into the string "2", and a string has been appended to it. Note that the operator precedence rules previously introduced still apply, as demonstrated in the second print statement.


<code-states-visualizer input='{"code":"public class Example {\n    public static void main(String[] args) {\n        System.out.println(\"Four: \" + (2 + 2));\n        System.out.println(\"But! Twenty-two: \" + 2 + 2);\n    }\n}","stdin":"","trace":[{"stdout":"","event":"call","line":3,"stack_to_render":[{"func_name":"main:3","encoded_locals":{},"ordered_varnames":[],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"1","frame_id":1}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":3,"stack_to_render":[{"func_name":"main:3","encoded_locals":{},"ordered_varnames":[],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"2","frame_id":2}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"Four: 4\n","event":"step_line","line":4,"stack_to_render":[{"func_name":"main:4","encoded_locals":{},"ordered_varnames":[],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"5","frame_id":5}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"Four: 4\nBut! Twenty-two: 22\n","event":"step_line","line":5,"stack_to_render":[{"func_name":"main:5","encoded_locals":{},"ordered_varnames":[],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"8","frame_id":8}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"Four: 4\nBut! Twenty-two: 22\n","event":"return","line":5,"stack_to_render":[{"func_name":"main:5","encoded_locals":{"__return__":["VOID"]},"ordered_varnames":["__return__"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"9","frame_id":9}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}}],"userlog":"Debugger VM maxMemory: 455M\n"}'></code-states-visualizer>

With the knowledge gained, we can combine text and variables to create an expression that is evaluated during printing:

```java
int x = 10;

System.out.println("The value of the variable x is: " + x);

int y = 5;
int z = 6;

System.out.println("y is " + y + " and z is " + z);
```

<sample-output>

The value of the variable x is: 10
y is 5 and z is 6

</sample-output>

<programming-exercise name="Sum of two numbers">

In this exercise, you will write a program that prompts the user for two numbers, then prints the sum of these numbers.

To start, we use a Scanner object to read input from the user, and assign each number to its own variable:

```java
Scanner scanner = new Scanner(System.in);

System.out.println("Give the first number:");
int first = scanner.nextInt();
System.out.println("Give the second number:");
int second = scanner.nextInt();

// do something with the numbers
```

The program is expected to produce the following outputs for the given inputs:

<sample-output>

Give the first number:
**8**
Give the second number:
**3**
The sum of the numbers is 11

</sample-output>

<sample-output>

Give the first number:
**3**
Give the second number:
**-1**
The sum of the numbers is 2

</sample-output>

</programming-exercise>

<programming-exercise name="Multiplication formula">

Write a program that requests two integers from the user and displays the formula and result of multiplying these two values.

The program should then display the calculation and result as follows:

<sample-output>

Give the first number:
**2**
Give the second number:
**8**
2 * 8 = 16

</sample-output>

<sample-output>

Give the first number:
**277**
Give the second number:
**111**
277 * 111 = 30747

</sample-output>

</programming-exercise>

## Division
The outcome of a division operation in programming depends on the data type of the variables involved. If all the variables are integers, the result will also be an integer, truncating any decimal points. For example, 3 / 2 would result in 1, which is the integer part of the real answer, 1.5. *This is different from what most people are used to, so it is important to be aware of this*.

However, if either the dividend or divisor is a floating-point number, the result will be a floating-point number as well. For example:

```java
double whenDividendIsFloat = 3.0 / 2;
System.out.println(whenDividendIsFloat); // prints 1.5

double whenDivisorIsFloat = 3 / 2.0;
System.out.println(whenDivisorIsFloat); // prints 1.5
```

An integer can be converted into a floating point number by placing a type-casting operation `(double)` before it:

```java
int first = 3;
int second = 2;

double result1 = (double) first / second;
System.out.println(result1); // prints 1.5

double result2 = first / (double) second;
System.out.println(result2); // prints 1.5
```

In general, the advice is to be careful when executing a division operation where both the dividend and divisor are integers. Another way to avoid this, is to convert one of the variables to a floating-point number by multiplying it with 1.0 before the division.

Another important point to note is that dividing by zero is usually undefined in programming, like in mathematics.

<programming-exercise name="Average of three numbers"  tmcname='part01-Part01_22.AverageOfThreeNumbers'>

Write a program that requests three integers from the user and calculates their average. The mathematical formula to find the average of x, y, and z is (x + y + z) / 3. Ensure that you take into consideration the rules of integer division when writing your code.

Example Output:

<sample-output>

Give the first number:
**8**
Give the second number:
**2**
Give the third number:
**3**
The average is 4.333333333333333

</sample-output>

<sample-output>

Give the first number:
**9**
Give the second number:
**5**
Give the third number:
**-1**
The average is 4.333333333333333

</sample-output>

</programming-exercise>

## Clarifying Misconceptions about the Value of a Variable
When a computer program is executed, each command is processed one command at a time, always advancing exactly as specified by the code. When a value is assigned to a variable, it follows a consistent pattern: the value on the right side of the equality sign is copied and assigned to the variable on the left-hand side (i.e. stored in the memory location specified by the variable on the left side). Understanding this is crucial for a programmer. However, there are common misunderstandings related to assigning values to variables:

* Mistakenly viewing value assignment as a transfer instead of a copy: After the statement first = second is executed, it is frequently assumed that the value of second has been transferred to first, and that second no longer holds a value or has a value of 0, for instance. This is incorrect as the statement first = second only copies the value stored in second to the memory location specified by first, leaving the value in second unchanged.

* Believing value assignment creates a dependency instead of being a copy: After the statement first = second is executed, it is sometimes thought that any changes made to the value of second are automatically reflected in the value of first. This is incorrect as value assignment is a one-time event that occurs only when the code first = second is executed.

* The third misunderstanding concerns the direction of copying: it's often thought that in executing `first = second` the value of the variable `first` is set as the value of the variable `second`. This confusion can also arise when the programmer writes, for example, 42 = value. Fortunately, many integrated development environments (IDEs) provide support for such issues.

A useful method for understanding the execution flow of a program is through the use of pen and paper. As you're reading the program, write down the names of any new variables and track the changes to their values as the code is processed line by line. For example, consider the following program code:

```java
line 1: int first = (1 + 1);
line 2: int second = first + 3 * (2 + 5);
line 3:
line 4: first = 5;
line 5:
line 6: int third = first + second;
line 7: System.out.println(first);
line 8: System.out.println(second);
line 9: System.out.println(third);
```

The following is a step-by-step explanation of the program's execution:

<sample-output>

line 1: initiate a variable first
line 1: copy the result of the calculation 1 + 1 as the value of the variable first
line 1: the value of the variable first is 2
line 2: create the variable second
line 2: calculate 2 + 5, 2 + 5 -> 7
line 2: calculate 3 * 7, 3 * 7 -> 21
line 2: calculate first + 21
line 2: copy the value of the variable first into the calculation, its value is 2
line 2: calculate 2 + 21, 2 + 21 -> 23
line 2: copy 23 to the value of the variable second
line 2: the value of the variable second is 23
line 3: (empty, do nothing)
line 4: copy 5 to the value of the variable first
line 4: the value of the variable first is 5
line 5: (empty, do nothing)
line 6: create variable third
line 6: calculate first + second
line 6: copy the value of the variable first into the calculation, its value is 5
line 6: calculate 5 + second
line 6: copy the value of the variable second into the calculation, its value is 23
line 6: calculate 5 + 23 -> 28
line 6: copy 28 to the value of the variable third
line 6: the value of the variable third is 28
line 7: print the variable first
line 7: copy the value of the variable first for the print operation, its value is 5
line 7: print the value 5
line 8: print the variable second
line 8: copy the value of the variable second for the print operation, its value is 23
line 8: print the value 23
line 9: print the variable third
line 9: copy the value of the variable third for the print operation, its value is 28
line 9: we print the value 28

</sample-output>

You'll find a step-by-step visualization of the previous program below, which goes through the program line by line -- on each step, reflect on how the program ends up with the result that it prints.

<code-states-visualizer input='{"code":"public class CalculationInSteps {\n  public static void main(String[] args) {\n    int first = (1 + 1);\n    int second = first + 3 * (2 + 5);\n\n    first = 5;\n\n    int third = first + second;\n    System.out.println(first);\n    System.out.println(second);\n    System.out.println(third);\n  }\n}","stdin":"","trace":[{"stdout":"","event":"call","line":3,"stack_to_render":[{"func_name":"main:3","encoded_locals":{},"ordered_varnames":[],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"1","frame_id":1}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":3,"stack_to_render":[{"func_name":"main:3","encoded_locals":{},"ordered_varnames":[],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"2","frame_id":2}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":4,"stack_to_render":[{"func_name":"main:4","encoded_locals":{"first":2},"ordered_varnames":["first"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"4","frame_id":4}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":6,"stack_to_render":[{"func_name":"main:6","encoded_locals":{"first":2,"second":23},"ordered_varnames":["first","second"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"9","frame_id":9}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":8,"stack_to_render":[{"func_name":"main:8","encoded_locals":{"first":5,"second":23},"ordered_varnames":["first","second"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"12","frame_id":12}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"","event":"step_line","line":9,"stack_to_render":[{"func_name":"main:9","encoded_locals":{"first":5,"second":23,"third":28},"ordered_varnames":["first","second","third"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"17","frame_id":17}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"5\n","event":"step_line","line":10,"stack_to_render":[{"func_name":"main:10","encoded_locals":{"first":5,"second":23,"third":28},"ordered_varnames":["first","second","third"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"21","frame_id":21}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"5\n23\n","event":"step_line","line":11,"stack_to_render":[{"func_name":"main:11","encoded_locals":{"first":5,"second":23,"third":28},"ordered_varnames":["first","second","third"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"24","frame_id":24}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"5\n23\n28\n","event":"step_line","line":12,"stack_to_render":[{"func_name":"main:12","encoded_locals":{"first":5,"second":23,"third":28},"ordered_varnames":["first","second","third"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"27","frame_id":27}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}},{"stdout":"5\n23\n28\n","event":"return","line":12,"stack_to_render":[{"func_name":"main:12","encoded_locals":{"first":5,"second":23,"third":28,"__return__":["VOID"]},"ordered_varnames":["first","second","third","__return__"],"parent_frame_id_list":[],"is_highlighted":true,"is_zombie":false,"is_parent":false,"unique_hash":"28","frame_id":28}],"globals":{},"ordered_globals":[],"func_name":"main","heap":{}}],"userlog":"Debugger VM maxMemory: 455M\n"}'></code-states-visualizer>
