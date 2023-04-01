---
path: "/week-6/3-separating-user-interface-from-program-logic"
title: "Separating the user interface from program logic"
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

 - Understand creating programs such that the user interface and the application logic are separated

 - Can create a textual user interface, which takes program specific application logic and a Scanner object as parameters

</text-box>

Let us explore the process of implementing a program and the importance of separating different areas of responsibility. Specifically, we will focus on a program that prompts the user to enter words until they repeat a word.

<sample-output>

Write a word: **carrot**
Write a word: **turnip**
Write a word: **potato**
Write a word: **celery**
Write a word: **potato**
You wrote the same word twice!

</sample-output>

To create this program, we'll need to build it step by step. However, one of the challenges we'll face is determining the best approach to take in solving the problem and deciding how to break it down into smaller subproblems. There is no definitive answer to this question, and it may depend on various factors, such as the problem domain and its concepts or the user interface.

One possible way to begin would be to focus on the user interface and develop a UserInterface class. This class would rely on a Scanner object to read user input. We can pass this object to the user interface so that it can process the input and provide appropriate feedback.

```java
public class UserInterface {
    private Scanner scanner;

    public UserInterface(Scanner scanner) {
        this.scanner = scanner;
    }

    public void start() {
        // do something
    }
}
```

Creating and starting up a user interface can be done as follows.

```java
public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    UserInterface userInterface = new UserInterface(scanner);
    userInterface.start();
}
```

## Looping and quitting

This program has (at least) two "sub-problems". The first problem is continuously reading words from the user until a certain condition is reached. We can outline this as follows.

```java
public class UserInterface {
    private Scanner scanner;

    public UserInterface(Scanner scanner) {
        this.scanner = scanner;
    }

    public void start() {

        while (true) {
            System.out.print("Enter a word: ");
            String word = scanner.nextLine();

            if (*stop condition*) {
                break;
            }

        }

        System.out.println("You gave the same word twice!");
    }
}
```

The current version of the program prompts the user for words until a repeat entry is detected. To achieve this, we need to modify the program to check if each entered word has already been submitted. However, we have yet to determine how this functionality will be implemented. Therefore, we will begin by creating an outline for the solution before proceeding with the actual implementation.

```java
public class UserInterface {
    private Scanner scanner;

    public UserInterface(Scanner scanner) {
        this.scanner = scanner;
    }

    public void start() {

        while (true) {
            System.out.print("Enter a word: ");
            String word = scanner.nextLine();

            if (alreadyEntered(word)) {
                break;
            }

        }

        System.out.println("You gave the same word twice!");
    }

    public boolean alreadyEntered(String word) {
        // do something here

        return false;
    }
}
```

It is a good idea to test the program continuously, so let's make a test version of the method:

```java
public boolean alreadyEntered(String word) {
    if (word.equals("end")) {
        return true;
    }

    return false;
}
```

Now the loop continues until the input equals the word "end":

<sample-output>

Enter a word: **carrot**
Enter a word: **celery**
Enter a word: **turnip**
Enter a word: **end**
You gave the same word twice!

</sample-output>

The program doesn't completely work yet, but the first sub-problem - quitting the loop when a certain condition has been reached - has now been implemented.

## Storing relevant information

Another sub-problem is remembering the already entered words. A list is a good structure for this purpose.

```java
public class UserInterface {
    private Scanner scanner;
    private List<String> words;

    public UserInterface(Scanner scanner) {
        this.scanner = scanner;
        this.words = new ArrayList<String>();
    }

    //...
}
```

When a new word is entered, it has to be added to the list of words that have been entered before. This is achieved by adding a line that updates our list to the while-loop:

```java
while (true) {
    System.out.print("Enter a word: ");
    String word = scanner.nextLine();

    if (alreadyEntered(word)) {
        break;
    }

    // adding the word to the list of previous words
    this.words.add(word);
}
```

The whole user interface looks as follows:

```java
public class UserInterface {
    private Scanner scanner;
    private List<String> words;

    public UserInterface(Scanner scanner) {
        this.scanner = scanner;
        this.words = new ArrayList<String>();
    }

    public void start() {

        while (true) {
            System.out.print("Enter a word: ");
            String word = scanner.nextLine();

            if (alreadyEntered(word)) {
                break;
            }

            // adding the word to the list of previous words
            this.words.add(word);

        }

        System.out.println("You gave the same word twice!");
    }

    public boolean alreadyEntered(String word) {
       if (word.equals("end")) {
            return true;
        }

        return false;
    }
}
```

Before proceeding with the actual implementation of the new functionality, it's a good practice to perform testing to ensure the program still functions correctly. One way to test the program is to include a print statement at the end of the start-method, confirming that the entered words have indeed been added to the list.

```java
// test print to check that everything still works
for (String word: this.words) {
    System.out.println(word);
}
```

## Combining the solutions to sub-problems

Let's change the method `alreadyEntered` such that it checks whether the entered word is contained in our list of already entered words.

```java
public boolean alreadyEntered(String word) {
    return this.words.contains(word);
}
```

Now the application works as intended.

## Objects as a natural part of problem solving

We just built a solution to a problem where the program reads words from a user until the user enters a word that has already been entered before. Our example input was as follows:

<sample-output>

Enter a word: **carrot**
Enter a word: **celery**
Enter a word: **turnip**
Enter a word: **potato**
Enter a word: **celery**
You gave the same word twice!

</sample-output>

We came up with the following solution:

```java
public class UserInterface {
    private Scanner scanner;
    private List<String> words;

    public UserInterface(Scanner scanner) {
        this.scanner = scanner;
        this.words = new ArrayList<String>();
    }

    public void start() {

        while (true) {
            System.out.print("Enter a word: ");
            String word = scanner.nextLine();

            if (alreadyEntered(word)) {
                break;
            }

            // adding the word to the list of previous words
            this.words.add(word);

        }

        System.out.println("You gave the same word twice!");
    }

    public boolean alreadyEntered(String word) {
       if (word.equals("end")) {
            return true;
        }

        return false;
    }
}
```

From the perspective of the user interface, the variable 'words' that we created earlier is merely a technical detail. What's more important is that the interface maintains a record of the *set of words* that the user has already entered. This set represents a distinct concept or abstraction, and it suggests that we can create an object to encapsulate this functionality. Whenever we encounter a clear abstraction like this, it's often useful to consider separating it into its own class.

### Word set

Let's make a class called `WordSet`. After implementing the class, the user interface's start method looks like this:

```java
while (true) {
    String word = scanner.nextLine();

    if (words.contains(word)) {
        break;
    }

    wordSet.add(word);
}

System.out.println("You gave the same word twice!");
```

From the perspective of the user interface, it's beneficial to encapsulate the functionality of maintaining and checking the set of words in a separate class called `Wordset`. This class should contain two methods: `boolean contains(String word)`, which checks if the given word is already present in the set, and `void add(String word)`, which adds the word to the set.

Organizing the functionality in this way can greatly improve the readability of the user interface, making it clearer and easier to understand. Below is an outline for the implementation of the 'WordSet' class.

```java
public class WordSet {
    // object variable(s)

    public WordSet() {
        // constructor
    }

    public boolean contains(String word) {
        // implementation of the contains method
        return false;
    }

    public void add(String word) {
        // implementation of the add method
    }
}
```

### Earlier solution as part of implementation

We can implement the set of words by changing our earlier solution, the list, into an object variable:

```java
import java.util.ArrayList;
import java.util.List;

public class WordSet {
    private List<String> words

    public WordSet() {
        this.words = new ArrayList<>();
    }

    public void add(String word) {
        this.words.add(word);
    }

    public boolean contains(String word) {
        return this.words.contains(word);
    }
}
```

Our solution is now much more elegant, having separated the distinct concept of maintaining a set of words into its own class. This encapsulates all the necessary details inside an object, leaving the user interface looking clean and easy to understand.

Next, we can update the user interface to utilize the `WordSet` class. Similar to how we passed the `Scanner` object as a parameter, we can also give the user interface an instance of `WordSet`. This enables the interface to call the `contains` and `add` methods on the set, allowing it to keep track of the words that the user has entered.

```java
public class UserInterface {
    private WordSet wordSet;
    private Scanner scanner;

    public userInterface(WordSet wordSet, Scanner scanner) {
        this.wordSet = wordSet;
        this.scanner = scanner;
    }

    public void start() {

        while (true) {
            System.out.print("Enter a word: ");
            String word = scanner.nextLine();

            if (this.wordSet.contains(word)) {
                break;
            }

            this.wordSet.add(word);
        }

        System.out.println("You gave the same word twice!");
    }
}
```

Starting the program is now done as follows:

```java
public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    WordSet set = new WordSet();

    UserInterface userInterface = new UserInterface(set, scanner);
    userInterface.start();
}
```

## Changing the implementation of a class

In our current implementation, the class 'WordSet' encapsulates a List. Is this a reasonable approach? It could be, as it allows us to make further changes to the class if necessary. For instance, if we want to save the word set into a file in the future, we can modify the class WordSet without changing the public interfaces used by the UserInterface class.

The key advantage of encapsulation is that changes made inside the WordSet class do not affect the UserInterface class. The UserInterface class accesses WordSet only through its public interfaces (methods), which shields it from any changes made to the implementation of WordSet.

## Implementing new functionality: palindromes

In the future, we may want to add new functionalities to the program through the class `WordSet`. For example, if we wanted to determine how many of the entered words were palindromes, we could add a method called 'palindromes' to the class.

```java
public void start() {

    while (true) {
        System.out.print("Enter a word: ");
        String word = scanner.nextLine();

        if (this.wordSet.contains(word)) {
            break;
        }

        this.wordSet.add(word);
    }

    System.out.println("You gave the same word twice!");
    System.out.println(this.wordSet.palindromes() + " of the words were palindromes.");
}
```

The user interface remains clean, because counting the palindromes is done inside the `WordSet` object. The following is an example implementation of the method:

```java
import java.util.ArrayList;
import java.util.List;

public class WordSet {
    private List<String> words;

    public WordSet() {
        this.words = new ArrayList<>();
    }

    public boolean contains(String word) {
        return this.words.contains(word);
    }

    public void add(String word) {
        this.words.add(word);
    }

    public int palindromes() {
        int count = 0;

        for (String word: this.words) {
            if (isPalindrome(word)) {
                count++;
            }
        }

        return count;
    }

    public boolean isPalindrome(String word) {
        int end = word.length() - 1;

        int i = 0;
        while (i < word.length() / 2) {
            // method charAt returns the character at given index
            // as a simple variable
            if(word.charAt(i) != word.charAt(end - i)) {
                return false;
            }

            i++;
        }

        return true;
    }
}
```

The method 'palindromes' uses the helper method `isPalindrome` to check whether the word that's given to it as a parameter is, in fact, a palindrome.

<text-box variant='hint' name='Recycling'>

Separating concepts into different classes in the code makes it easier to recycle and reuse them in other projects. For instance, the class `WordSet` could be used in a graphical user interface or as part of a mobile phone application. Furthermore, dividing the program into several concepts makes testing easier as each unit can function separately with its own logic.

</text-box>

## Programming tips

In the larger example above, we were following the advice given here.

-  Proceed with small steps
    -  Try to separate the program into several sub-problems and **work on only one sub-problem at a time**
    -  Always test that the program code is advancing in the right direction, in other words: test whether the solution to the sub-problem is correct
    -  Recognize the conditions that require the program to work differently. In the example above, we needed a different functionality to test whether a word had been already entered before.

-  Write as "clean" code as possible
    -  Indent your code
    -  Use descriptive method and variable names
    -  Don't make your methods too long, not even the main method
    -  Do only one thing inside one method
    -  **Remove all copy-paste code**
    -  Replace the "bad" and unclean parts of your code with clean code

-  If needed, it's also a good idea to step back and assess the program as a whole. If it's not working, we might need to go back to a previous state where the code was still functional. As a rule, adding more code to a broken program rarely fixes it.

By following these practices, we can make our code more reusable and maintainable. We can also ensure that our programs work as intended and are easier to modify and test.

<programming-exercise name='To do list (2 parts)'>

In this exercise we are going to create a program that can be used to create and modify a to-do list. The final product will work in the following manner.

<sample-output>

Command: **add**
Task: **go to the store**
Command: **add**
Task: **vacuum clean**
Command: **list**
1: go to the store
2: vacuum clean
Command: **completed**
Which task was completed? **2**
Task go to the store tehty
Command: **list**
1: go to the store
Command: **add**
Task: **program**
Command: **list**
1: go to the store
2: program
Command: **stop**

</sample-output>

We will build the program in parts.

<h2>TodoList</h2>

Create a class called `TodoList`. It should have a constructor without parameters and the following methods:

- `public void add(String task)` - adds the task passed as a parameter to the to-do list.
- `public void print()` - prints the exercises. Each task has a number associated with it on the print statement -- use the task's index here (+1).
- `public void remove(int number)` - removes the task associated with the given number; the number is the one seen associated with the task in the print.

```java
TodoList list = new TodoList();
list.add("read the course material");
list.add("watch the latest fool us");
list.add("take it easy");

list.print();
list.remove(2);

System.out.println();
list.print();
```

<sample-output>

1: read the course material
2: watch the latest fool us
3: take it easy

1: read the course material
2: take it easy

</sample-output>

**NB!** You may assume that the `remove` method is given a number that corresponds to a real task. The method only has to correctly work once after each print call.

Another example:

```java
TodoList list = new TodoList();
list.add("read the course material");
list.add("watch the latest fool us");
list.add("take it easy");
list.print();
list.remove(2);
list.print();
list.add("buy raisins");
list.print();
list.remove(1);
list.remove(1);
list.print();
```

<sample-output>

1: read the course material
2: watch the latest fool us
3: take it easy
1: read the course material
2: take it easy
1: read the course material
2: take it easy
3: buy raisins
1: buy raisins

</sample-output>

<h2>User interface</h2>

Next, create a class called `UserInterface` with a constructor that takes in two parameters. The first parameter is an instance of the `TodoList` class, and the second parameter is an instance of the `Scanner` class. The class should also contain a method called `public void start()` which will initiate the text user interface.

The text user interface should have an eternal looping statement using `while-true`. It should offer the following commands to the user:

- The command `stop` stops the execution of the loop, after which the execution of the program advances out of the `start` method.

- The command `add` asks the user for the next task to be added. Once the user enters this task, it should be added to the to-do list.

- The commmand `list` prints all the tasks on the to-do list.

- The command `remove` asks the user to enter the id of the task to be removed. When this has been entered, the specified task should be removed from the list of tasks.

Below is an example of how the program should work.

<sample-output>

Command: **add**
To add: **write an essay**
Command: **add**
To add: **read a book**
Command: **list**
1: write an essay
2: read a book
Command: **remove**
Which one is removed? **1**
Command: **list**
1: read a book
Command: **remove**
Which one is removed? **1**
Command: **list**
Command: **add**
To add: **stop**
Command: **list**
1: stop
Command: **stop**

</sample-output>

NB! The user interface is to use the TodoList and Scanner that are passed as parameters to the constructor.


</programming-exercise>

## From one entity to many parts

Consider a program that prompts the user to enter exam points and converts them into grades. The program also displays the grade distribution using stars. The program terminates when the user inputs an empty string. An example implementation of the program is shown below:

<sample-output>

Points: **91**
Points: **98**
Points: **103**
Impossible number.
Points: **90**
Points: **89**
Points: **89**
Points: **88**
Points: **72**
Points: **54**
Points: **55**
Points: **51**
Points: **49**
Points: **48**
Points:

5: \*\*\*
4: \*\*\*
3: \*
2:
1: \*\*\*
0: \*\*

</sample-output>

As almost all programs, this program can be written into `main` as one entity. Here is one possibility:

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Program {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        List<Integer> grades = new ArrayList<>();

        while (true) {
            System.out.print("Points: ");
            String input = scanner.nextLine();
            if (input.equals("")) {
                break;
            }

            int score = Integer.valueOf(input);

            if (score < 0 || score > 100) {
                System.out.println("Impossible number.");
                continue;
            }

            int grade = 0;
            if (score < 50) {
                grade = 0;
            } else if (score < 60) {
                grade = 1;
            } else if (score < 70) {
                grade = 2;
            } else if (score < 80) {
                grade = 3;
            } else if (score < 90) {
                grade = 4;
            } else {
                grade = 5;
            }

            grades.add(grade);
        }

        System.out.println("");
        int grade = 5;
        while (grade >= 0) {
            int stars = 0;
            for (int received: grades) {
                if (received == grade) {
                    stars++;
                }
            }

            System.out.print(grade + ": ");
            while (stars > 0) {
                System.out.print("*");
                stars--;
            }
            System.out.println("");

            grade = grade - 1;
        }
    }
}
```

To break down the program into more manageable parts, we can identify distinct areas of responsibility within the program. For instance, managing grades, which involves converting scores into grades, could be isolated in a separate class. Similarly, we could create another class specifically for the user interface.

### Program logic

The program logic includes parts that are crucial for the execution of the program, like functionalities that store information. Using the previous example, we can separate the parts that store grade information and create a class called `GradeRegister`. This class will be responsible for keeping track of the number of different grades students have received. We can add grades to the register according to scores and use the register to ask how many people have received a certain grade.

An example class follows:

```java
import java.util.ArrayList;
import java.util.List;


public class GradeRegister {

    private List<Integer> grades;

    public GradeRegister() {
        this.grades = new ArrayList<>();
    }

    public void addGradeBasedOnPoints(int points) {
        this.grades.add(pointsToGrades(points));
    }

    public int numberOfGrades(int grade) {
        int count = 0;
        for (int received: this.grades) {
            if (received == grade) {
                count++;
            }
        }

        return count;
    }

    public static int pointsToGrades(int points) {

        int grade = 0;
        if (points < 50) {
            grade = 0;
        } else if (points < 60) {
            grade = 1;
        } else if (points < 70) {
            grade = 2;
        } else if (points < 80) {
            grade = 3;
        } else if (points < 90) {
            grade = 4;
        } else {
            grade = 5;
        }

        return grade;
    }
}
```

When the grade register has been separated into a class, we can remove the functionality associated with it from our main program. The main program now looks like this.


```java
import java.util.Scanner;

public class Program {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        GradeRegister register = new GradeRegister();

        while (true) {
            System.out.print("Points: ");
            String input = scanner.nextLine();
            if (input.equals("")) {
                break;
            }

            int score = Integer.valueOf(input);

            if (score < 0 || score > 100) {
                System.out.println("Impossible number.");
                continue;
            }

            register.addGradeBasedOnPoints(score);
        }

        System.out.println("");
        int grade = 5;
        while (grade >= 0) {
            int stars = register.numberOfGrades(grade);
            System.out.print(grade + ": ");
            while (stars > 0) {
                System.out.print("*");
                stars--;
            }
            System.out.println("");

            grade = grade - 1;
        }
    }
}
```

Separating the program's logic into different classes offers significant benefits for program maintenance. By separating the GradeRegister into its own class, it can be tested independently of the rest of the program. Additionally, the GradeRegister can be copied and used in other programs.

```java
GradeRegister register = new GradeRegister();
register.addGradeBasedOnPoints(51);
register.addGradeBasedOnPoints(50);
register.addGradeBasedOnPoints(49);

System.out.println("Number of students with grade 0 (should be 1): " + register.numberOfGrades(0));
System.out.println("Number of students with grade 0 (should be 2): " + register.numberOfGrades(2));
```

### User interface

In general, each program has its own user interface. Therefore, we will create a separate class called `UserInterface` and decouple it from the main program. The constructor of the `UserInterface` class will take two parameters: a grade register for storing the grades and a `Scanner` object that reads user input.

With a separate user interface in place, the main program that initializes the entire application becomes more straightforward.

```java
import java.util.Scanner;

public class Program {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        GradeRegister register = new GradeRegister();

        UserInterface userInterface = new UserInterface(register, scanner);
        userInterface.start();
    }
}
```

Let's have a look at how the user interface is implemented. There are two essential parts to the UI: reading the points, and printing the grade distribution.

```java
import java.util.Scanner;

public class UserInterface {

    private GradeRegister register;
    private Scanner scanner;

    public UserInterface(GradeRegister register, Scanner scanner) {
        this.register = register;
        this.scanner = scanner;
    }

    public void start() {
        readPoints();
        System.out.println("");
        printGradeDistribution();
    }

    public void readPoints() {
    }

    public void printGradeDistribution() {
    }
}
```

It's possible to reuse the code for reading exam points and printing grade distribution from the previous main program with minimal modifications. In the following program, some parts of the code have indeed been copied from the earlier version, while a new method for printing stars has been added to improve the clarity of the code that prints the grade distribution.

```java
import java.util.Scanner;

public class UserInterface {

    private GradeRegister register;
    private Scanner scanner;

    public UserInterface(GradeRegister register, Scanner scanner) {
        this.register = register;
        this.scanner = scanner;
    }

    public void start() {
        readPoints();
        System.out.println("");
        printGradeDistribution();
    }

    public void readPoints() {
        while (true) {
            System.out.print("Points: ");
            String input = scanner.nextLine();
            if (input.equals("")) {
                break;
            }

            int points = Integer.valueOf(input);

            if (points < 0 || points > 100) {
                System.out.println("Impossible number.");
                continue;
            }

            this.register.addGradeBasedOnPoints(points);
        }
    }

    public void printGradeDistribution() {
        int grade = 5;
        while (grade >= 0) {
            int stars = register.numberOfGrades(grade);
            System.out.print(grade + ": ");
            printStars(stars);
            System.out.println("");

            grade = grade - 1;
        }
    }

    public static void printStars(int stars) {
        while (stars > 0) {
            System.out.print("*");
            stars--;
        }
    }
}
```


<programming-exercise name='Averages (3 parts)'>

The exercise base includes the previously constructed program to store grades. In this exercise you will further develop the class `GradeRegister` so that it can calculate the average of grades and exam results.

<h2>Average grade</h2>

Create the method `public double averageOfGrades()` for the class `GradeRegister`. It should return the average of the grades. If the register contains no grades, the method should return `-1`. Use the `grades` list to calculate the average.

Example:

```java
GradeRegister register = new GradeRegister();
register.addGradeBasedOnPoints(93);
register.addGradeBasedOnPoints(91);
register.addGradeBasedOnPoints(92);
register.addGradeBasedOnPoints(88);

System.out.println(register.averageOfGrades());
```

<sample-output>

4.75

</sample-output>

<h2>Average points</h2>

Give the class `GradeRegister` a new object variable: a list where you will store the exam points every time that the method `addGradeBasedOnPoints` is called. After this addition, create a method `public double averageOfPoints()` that calculates and returns the average of the exam points. If there are no points added to the register, the method should return the number `-1`.

Example:

```java
GradeRegister register = new GradeRegister();
register.addGradeBasedOnPoints(93);
register.addGradeBasedOnPoints(91);
register.addGradeBasedOnPoints(92);

System.out.println(register.averageOfPoints());
```

<sample-output>

92.0

</sample-output>

<h2>Prints in the user interface</h2>

As a final step, add the methods implemented above as parts of the user interface. When the program prints the grade distribution, it should also print the averages of the points and the grades.

<sample-output>

Points: **82**
Points: **83**
Points: **96**
Points: **51**
Points: **48**
Points: **56**
Points: **61**
Points:

5: \*
4: \*\*
3:
2: \*
1: \*\*
0: \*
The average of points: 68.14285714285714
The average of grades: 2.4285714285714284

</sample-output>

</programming-exercise>
