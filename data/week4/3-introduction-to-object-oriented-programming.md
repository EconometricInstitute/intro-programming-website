---
path: "/week-4/3-introduction-to-object-oriented-programming"
title: "Introduction to object-oriented programming"
hidden: false
---

<text-box variant='learningObjectives' name='Learning Objectives'>

- You are familiar with the concepts of class, object, constructor, object methods, and object variables.

- You understand that a class defines an object's methods and that the values of instance (object) variables are object-specific.

- You know how to create classes and objects, and know how to use objects in your programs.

</text-box>

Let's dive into the basics of object-oriented programming, a programming style that helps us organize and manage our code more effectively. We will focus on representing ideas and information with objects, and then add functionality to our program using methods.

Object-oriented programming (OOP) is a way to break down complex problems into smaller, more manageable pieces. It does this by representing the different aspects of a problem as separate entities called objects. By doing this, we can create abstractions that simplify the problem-solving process.

To begin with, we identify the main ideas or components related to a problem. We then create structures in our code, called classes, to represent these ideas. Classes are like blueprints for creating objects, which are the actual instances of these ideas in our programs. These objects help us tackle the problem at hand by interacting and cooperating with one another.

The idea that "programs are built from small, clear, and cooperative objects" might not make perfect sense right now, but as we explore object-oriented programming further, this concept will become clearer and more intuitive.

## Classes and Objects
We have already utilized some of Java's classes and objects. A **class** defines an object's attributes, such as its related information (instance variables), and its methods or commands. The object's internal state is determined by the values of its instance variables, while its functionality is determined by its methods.

A **Method** is a named piece of source code that can be called and is typically written inside a class. A method is always associated with a class and is frequently employed to modify the internal state of an instantiated object.

For example, Java's `ArrayList` class has been employed in our programs, with objects instantiated from it. Below, we create an `ArrayList` object named `integers` and add several integers to it.

```java
// we create an object from the ArrayList class named integers
ArrayList<Integer> integers = new ArrayList<>();

// let's add the values 15, 34, 65, 111 to the integers object
integers.add(15);
integers.add(34);
integers.add(65);
integers.add(111);

// we print the size of the integers object
System.out.println(integers.size());
```

An object is always instantiated by calling a method that created an object, i.e., a **constructor** by using the `new` keyword.

<text-box variant='hint' name='The Relationship Between a Class and an Object'>

A class lays out a blueprint for any objects that are instantiated from it. Let's draw from an analogy from outside the world of computers. Detached houses are most likely familiar to most, and we can safely assume the existence of drawings somewhere that determine what exactly a detached house is to be like. A class is a blueprint. In other words, it specifies what kinds of objects can be instantiated from it.

<img src="../img/rintamamiestalo-rakennuspiirrustus.jpg"/>

Individual objects (detached houses in this case) are all created based on the same blueprints - they're instances of the same class. The states of individual objects, i.e., their attributes (such as the wall color, the building material of the roof, the color of its foundations, the doors' materials and color, ...) may all vary, however. The following is an "object of a detached-house class":

<img src="../img/rintamamiestalo.jpg" />

</text-box>

<programming-exercise name='Your first account'>

The exercise template comes with a ready-made class named `Account`. The `Account` object represents a bank account that has balance (i.e. one that has some amount of money in it). The accounts are used as follows:

```java
Account artosAccount = new Account("Arto's account", 100.00);
Account artosSwissAccount = new Account("Arto's account in Switzerland", 1000000.00);

System.out.println("Initial state");
System.out.println(artosAccount);
System.out.println(artosSwissAccount);

artosAccount.withdraw(20);
System.out.println("The balance of Arto's account is now: " + artosAccount);
artosSwissAccount.deposit(200);
System.out.println("The balance of Arto's other account is now: " + artosSwissAccount);

System.out.println("End state");
System.out.println(artosAccount);
System.out.println(artosSwissAccount);
```

Write a program that creates an account with a balance of 100.0, deposits 20.0 in it, and finally prints the balance. **NB!** Perform all the operations in this exact order.

</programming-exercise>

## Creating Classes

In programming, a class defines the properties and behaviors of objects instantiated from it. The object's variables, also known as instance variables, describe the object's internal state, while its methods describe what the object can do.

To create our own classes, we need to define the variables that belong to them. We usually define a class to represent a meaningful entity, which can be a real-world object or concept. For example, if our program needs to process personal information, we can define a separate `Person` class consisting of methods and attributes related to an individual.

Now, let's get started. Assume that we have a project template that has an empty main program:

```java
public class Main {

    public static void main(String[] args) {

    }
}
```
<text-box variant='hint' name='Creating a New Class'>

In IntelliJ, a new class can be created by going to the _project_ tab located on the left, right-clicking _New_, and then selecting _Java Class_. The class is provided a name in the dialog that opens, where you should select the default _Class_ option.

As with variables and methods, the name of a class should be as descriptive as possible. It's usual for a class to live on and take on a different form as a program develops. As such, the class may have to be renamed at some later point.

</text-box>

Let us create a class named `Person`, for which we need to create a separate file called `Person.java`. As a result, our program will consist of two separate files, with the main program remaining in its own file. The `Person.java` file should initially contain the class definition, which is denoted by the keyword `public class Person`, along with the curly brackets that contain the class's contents.

```java
public class Person {

}
```

You can also draw a class diagram to depict a class. We'll become familiar with its notations as we go along. An empty person-named class looks like this:

<img src="../img/diagrams/part4.1-classdiagram-person.png">

A class defines the attributes and behaviors of objects that are instantiated from it. For our `Person` class, let's specify that each person object has a name and an age. We can represent the name as a string and the age as an integer. Let's add these attributes to our class blueprint:

```java
public class Person {
    private String name;
    private int age;
}
```

As mentioned earlier, each object created from the `Person` class has a `name` and an `age`. These variables are called **instance variables**, object fields, or object attributes.

To define these instance variables, we write them on separate lines following the class definition `public class Person {`. Each variable should be preceded by the **private** keyword. This keyword indicates that the variables are "hidden" inside the object and **encapsulated** within the class.

In a class diagram, the variables associated with the class are denoted as "variableName: variableType". The minus sign preceding the variable name indicates that the variable is encapsulated, meaning it has the `private` keyword.

<img src="../img/diagrams/part4.1-classdiagram-person-name-age.png">

We have now defined a blueprint -- a class -- for the `Person` object. Each new `Person` object has the variables `name` and `age`, which are able to hold object-specific values. The "state" of a person consists of the values assigned to their name and age.

## Defining a Constructor
To set an initial state for an object when it's created, we can use the `new` keyword to create a new instance of the object. Similar to objects created from pre-made Java classes, such as `ArrayList`, we can pass values to the variables of our `Person` object during instantiation.

For instance, when creating a new `Person` object, it's convenient to provide it with a name. Here's an example of how to do this:

```java
public static void main(String[] args) {
    Person ada = new Person("Ada");
    // ...
}
```

The process of creating this object is accomplished by defining a method, known as the constructor. The constructor is defined after the instance variables. Here is an example: consider the Person class, for which a constructor is defined to create a new Person object. Upon instantiation, the constructor initializes the age of the object to 0, and sets the name of the object to the string passed as a parameter.

```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }
}
```

The constructor in any class must have the same name as the class. In the aforementioned Person class, the constructor will also be named Person. When defining the constructor, it is important to note that it takes in the name of the person object to be created as a parameter enclosed in parentheses following the constructor's name. Optional parameters are enclosed in parentheses and are followed by curly braces, which contain the program's source code executed when the constructor is called (e.g., `new Person("Ada")`).

It's worth noting that objects are always created using constructors. In the given example, the constructor includes the expression `this.age = 0`, which assigns a value of 0 to the newly created object's instance variable `age`. Similarly, `this.name = initialName` assigns the passed string as a parameter to the instance variable `name` of the created object.

<img src="../img/diagrams/part4.1-classdiagram-person-name-age-constructor.png">

<text-box variant='hint' name='Default Constructor'>

Java provides a default constructor for a class if the programmer does not define one. This default constructor does not perform any operations apart from creating the object. As a result, the object's variables remain uninitialized, and any object references will be `null`, meaning they do not point to anything. The values of primitives will be set to `0`.



For example, an object can be created from the class below by making the call `new Person()`

```java
public class Person {
    private String name;
    private int age;
}
```

If a constructor has already been defined for a class, no default constructor exists for that class. Therefore, if `new Person()` were to be called for the class below, an error would occur as Java cannot find a constructor in the class that does not take any parameters:



```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }
}
```

</text-box>

## Defining Methods For an Object
Creating an object and initializing its variables is just the first step in using an object. To enable an object to perform operations, it must also have methods defined. A **method** is a named section of source code inside a class that can be called upon to execute certain tasks.



```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }

    public void printPerson() {
        System.out.println(this.name + ", age " + this.age + " years");
    }
}
```

A method is written inside the class, typically beneath the constructor. The method name is preceded by `public void`, since the method is intended to be visible to the outside world (`public`), and not return a value (`void`).

<text-box variant='hint' name='Objects and the Static Modifier'>

We've used the modifier `static` in some methods that we've written. The `static` modifier indicates that the method in question does not belong to an object and thus cannot be used to access any variables that belong to objects.

Going forward, our methods will not include the `static` keyword if they're used to process information about objects created form a given class. If a method receives as parameters all the variables whose values ​​it uses, it can have the `static` modifier.

</text-box>

In addition to the class name, instance variables, and constructor, the class diagram now includes a new method called `printPerson`. In the diagram, the method is denoted with a `+` symbol preceding its name, indicating that it is a `public` method. Since the method takes no parameters, an empty set of parentheses is included after the method name. Finally, the method is marked with the keyword `void`, indicating that it does not return any value.



<img src="../img/diagrams/part4.1-classdiagram-person-name-age-constructor-print.png">

The `printPerson` method contains a single line of code that uses the instance variables `name` and `age` of the object. The internal implementation of the method is not specified in the class diagram. Instance variables are accessed using the `this` keyword, which refers to the current object. All of the object's variables are visible and accessible from within the method.

To demonstrate this method, we can create three `Person` objects in the main program and call the `printPerson` method on each object to print its details:

```java
public class Main {

    public static void main(String[] args) {
        Person ada = new Person("Ada");
        Person antti = new Person("Antti");
        Person martin = new Person("Martin");

        ada.printPerson();
        antti.printPerson();
        martin.printPerson();
    }
}
```
Prints:

<sample-output>

Ada, age 0 years
Antti, age 0 years
Martin, age 0 years

</sample-output>


<programming-exercise name='Door'>

Create a class named `Door`. The door does not have any variables. Create a constructor for it with no parameters (or use the default constructor). After that, create a `public void knock()` method for the door that prints the message "Who's there?" when called.

The door should work as follows.

```java
Door alexander = new Door();

alexander.knock();
alexander.knock();
```

<sample-output>

Who's there?
Who's there?

</sample-output>

</programming-exercise>

<programming-exercise name='Product'>

Create a class `Product` that represents a store product. The product should have a price (double), a quantity (int) and a name (String).

The class should have:

- the constructor `public Product (String initialName, double initialPrice, int initialQuantity)`
- a method `public void printProduct()` that prints product information in the following format:

<sample-output>

Banana, price 1.1, 13 pcs

</sample-output>

The output above is based on the product being assigned the name `Banana`, with a price of `1.1`, and a quantity of `13` .

</programming-exercise>


## Changing an Instance Variable's Value in a Method
Let's add a method to the previously created `Person` class that increments the age of the person by a year.

```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }

    public void printPerson() {
        System.out.println(this.name + ", age " + this.age + " years");
    }

    // growOlder() method has been added
    public void growOlder() {
        this.age = this.age + 1;
    }
}
```

The method is written inside the `Person` class, just as the `printPerson` method was. The method increments the value of the instance variable `age` by one.

The class diagram also gets an update.

<img src="../img/diagrams/part4.1-classdiagram-person-name-age-constructor-print-grow.png">

Let's call the method and see what happens:

```java
public class Main {

    public static void main(String[] args) {
        Person ada = new Person("Ada");
        Person antti = new Person("Antti");

        ada.printPerson();
        antti.printPerson();
        System.out.println("");

        ada.growOlder();
        ada.growOlder();

        ada.printPerson();
        antti.printPerson();
    }
}
```

The program's print output is as follows:

<sample-output>

Ada, age 0 years
Antti, age 0 years

Ada, age 2 years
Antti, age 0 years

</sample-output>

That is to say that when the two objects are "born" they are both zero years old (`this.age = 0;` is executed in the constructor). The `ada` object's `growOlder` method is called twice. As the print output demonstrates, the age of Ada is 2 years after growing older. Calling the method on an object corresponding to Ada has no impact on the age of the other person object, since each object instantiated form a class has its own instance variables.

The method can also contain conditional statements and loops. The `growOlder` method below limits aging to 30 years.

```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }

    public void printPerson() {
        System.out.println(this.name + ", age " + this.age + " years");
    }

    // no one exceeds the age of 30
    public void growOlder() {
        if (this.age < 30) {
            this.age = this.age + 1;
        }
    }
}
```

<programming-exercise name='Debt'>

Create the class `Debt` that has double-typed instance variables of `balance` and `interestRate`. The balance and the interest rate are passed to the constructor as parameters `public Debt(double initialBalance, double initialInterestRate)`.

In addition, create the methods `public void printBalance()` and `public void waitOneYear()` for the class. The method `printBalance` prints the current balance, and the `waitOneYear` method grows the debt amount.

The debt is increased by multiplying the balance by the interest rate.

The class should do the following:

```java
public class MainProgram {
    public static void main(String[] args) {

        Debt mortgage = new Debt(120000.0, 1.01);
        mortgage.printBalance();

        mortgage.waitOneYear();
        mortgage.printBalance();

        int years = 0;

        while (years < 20) {
            mortgage.waitOneYear();
            years = years + 1;
        }

        mortgage.printBalance();
    }
}
```

The example above illustrates the development of a mortgage with an interest rate of one percent.

Prints:

<sample-output>

120000.0
121200.0
147887.0328416936

</sample-output>

Once you get the program to work, try out the previous example with the interest rates of the early 1990s recession when the interest rates were as high as 15-20% - try swapping the interest rate in the example above with `1.20` and see what happens.

</programming-exercise>

## Returning a Value From a Method
A value can be returned by a method. However, the methods that have been created in our objects until now have not returned anything, as indicated by the keyword **void** in their method definition.



```java
public class Door {
    public void knock() {
        // ...
    }
}
```

The keyword **void** means that the method does not return a value.

To enable a method to return a value, the `void` keyword in the method signature must be replaced with the type of variable that will be returned. The following example demonstrates how the `grade` method in the `Teacher` class returns an integer (`int`) variable, which is always set to the value of 10 using the `return` statement:

```java
public class Teacher {
    public int grade() {
        return 10;
    }
}
```

When called, the method mentioned above returns an `int` type variable with a value of 10. To use the returned value, it must be assigned to a variable using the equals sign, just like regular value assignment. Here is an example of how this can be done:


```java
public static void main(String[] args) {
    Teacher teacher = new Teacher();

    int grading = teacher.grade();

    System.out.println("The grade received is " + grading);
}
```

<sample-output>

The grade received is 10

</sample-output>

The method's return value is assigned to a variable of type `int` value just as any other `int` value would be. The return value could also be used to form part of an expression.

```java
public static void main(String[] args) {
    Teacher first = new Teacher();
    Teacher second = new Teacher();
    Teacher third = new Teacher();

    double average = (first.grade() + second.grade() + third.grade()) / 3.0;

    System.out.println("Grading average " + average);
}
```

<sample-output>

Grading average 10.0

</sample-output>

All the variables we've encountered so far can also be returned by a method. To summarize:

- A method that returns nothing has the `void` modifier as the type of variable to be returned.

```java
public void methodThatReturnsNothing() {
    // the method body
}
```

- A method that returns an integer variable has the `int` modifier as the type of variable to be returned.

```java
public int methodThatReturnsAnInteger() {
    // the method body, requires a return statement
}
```

- A method that returns a string has the `String` modifier as the type of the variable to be returned

```java
public String methodThatReturnsAString() {
    // the method body, requires a return statement
}
```

- A method that returns a double-precision number has the `double` modifier as the type of the variable to be returned.

```java
public double methodThatReturnsADouble() {
    // the method body, requires a return statement
}
```

Let's continue with the `Person` class and add a `returnAge` method that returns the person's age.

```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }

    public void printPerson() {
        System.out.println(this.name + ", age " + this.age + " years");
    }

    public void growOlder() {
        if (this.age < 30) {
            this.age = this.age + 1;
        }
    }
    // the added method
    public int returnAge() {
        return this.age;
    }
}
```

So the class in its entirety is structured as follows:

<img src="../img/diagrams/part4.1-classdiagram-person-name-age-constructor-print-grow-return.png" alt="[Henkilo|-nimi:String;-ika:int|+Henkilo(String);+tulostaHenkilo():void;+vanhene():void;+palautaIka():int]">

Let's illustrate how the method works:

```java
public class Main {

    public static void main(String[] args) {
        Person pekka = new Person("Pekka");
        Person antti = new Person("Antti");

        pekka.growOlder();
        pekka.growOlder();

        antti.growOlder();

        System.out.println("Pekka's age: " + pekka.returnAge());
        System.out.println("Antti's age: " + antti.returnAge())
        int combined = pekka.returnAge() + antti.returnAge();

        System.out.println("Pekka's and Antti's combined age " + combined + " years");
    }
}
```

<sample-output>

Pekka's age 2
Antti's age 1

Pekka's and Antti's combined age 3 years

</sample-output>

As we have observed, methods can include any valid source code, such as conditionals, loops, and calls to other methods. In this example, we will create a method that checks if a person is of legal age and returns a `boolean` value (`true` if they are of legal age, and `false` if they are not).

```java
public class Person {
    // ...

    public boolean isOfLegalAge() {
        if (this.age < 18) {
            return false;
        }

        return true;
    }

    /*
     The method could have been written more succintly in the following way:

    public boolean isOfLegalAge() {
        return this.age >= 18;
    }
    */
}
```

And let's test it out:

```java
public static void main(String[] args) {
    Person pekka = new Person("Pekka");
    Person antti = new Person("Antti");

    int i = 0;
    while (i < 30) {
        pekka.growOlder();
        i = i + 1;
    }

    antti.growOlder();

    System.out.println("");

    if (antti.isOfLegalAge()) {
        System.out.print("of legal age: ");
        antti.printPerson();
    } else {
        System.out.print("underage: ");
        antti.printPerson();
    }

    if (pekka.isOfLegalAge()) {
        System.out.print("of legal age: ");
        pekka.printPerson();
    } else {
        System.out.print("underage: ");
        pekka.printPerson();
    }
}
```

<sample-output>

underage: Antti, age 1 years
of legal age: Pekka, age 30 years

</sample-output>

In the previous example, the `Person` class could only be printed in a way that included both the name and the age. However, in some situations, we may only need to know the name of an object. To address this need, we can create a separate method that returns only the name of the `Person` object. This method can be called from other parts of our program to obtain the name of the object without including the age. This added flexibility allows us to choose whether to display only the name or both the name and the age, depending on the needs of our program.

```java
public class Person {
    // ...

    public String getName() {
        return this.name;
    }
}
```

In Java, it is customary to name a method that returns an instance variable using the `getVariableName` naming convention. Such methods are called "getters". In the context of the `Person` class, `getName` is a more appropriate method name that conforms to this convention. Using this naming convention creates a more intuitive API, makes the code more readable, and is easier for other programmers to understand.

The class as a whole is now as follows:

<img src="../img/diagrams/part4.1-classdiagram-person-getters.png" alt="[Henkilo|-nimi:String;-ika:int|+Henkilo(String);+tulostaHenkilo():void;+vanhene():void;+palautaIka():int;+taysiIkainen():boolean;+getNimi():String]">


Let's mould the main program to use the new "getter" method:

```java
public static void main(String[] args) {
    Person pekka = new Person("Pekka");
    Person antti = new Person("Antti");

    int i = 0;
    while (i < 30) {
        pekka.growOlder();
        i = i + 1;
    }

    antti.growOlder();

    System.out.println("");

    if (antti.isOfLegalAge()) {
        System.out.println(antti.getName() + " is of legal age");
    } else {
        System.out.println(antti.getName() + " is underage");
    }

    if (pekka.isOfLegalAge()) {
        System.out.println(pekka.getName() + " is of legal age");
    } else {
        System.out.println(pekka.getName() + " is underage ");
    }
}
```

The print output is starting to turn out quit neat:

<sample-output>

Antti is underage
Pekka is of legal age

</sample-output>

<programming-exercise name='Gauge'>

Create the class `Gauge`. The gauge has the instance variable `private int value`, a constructor without parameters (sets the initial value of the meter variable to 0), and also the following four methods:

- Method `public void increase()` grows the `value` instance variable's value by one. It does not grow the value beyond five.
- Method `public void decrease()` decreases the `value` instance variable's value by one. It does not decrease the value to negative numbers.
- Method `public int value()` returns the `value` variable's value.
- Method `public boolean full()` returns `true` if the instance variable `value` has the value five. Otherwise, it returns false.

An example of the class in use.

```java
Gauge g = new Gauge();

while(!g.full()) {
    System.out.println("Not full! Value: " + g.value());
    g.increase();
}

System.out.println("Full! Value: " + g.value());
g.decrease();
System.out.println("Not full! Value: " + g.value());

```

<sample-output>

Not full! Value: 0
Not full! Value: 1
Not full! Value: 2
Not full! Value: 3
Not full! Value: 4
Full! Value: 5
Not full! Value: 4

</sample-output>

</programming-exercise>

## A string representation of an object and the toString-method
In the previous example, we created a `printPerson` method to print the `Person` object, which is not considered good programming practice. A better approach is to define a method for the object that returns a "string representation" of the object, which is achieved by defining the `toString` method in Java. Let's define this method for the person in the following example:

```java
public class Person {
    // ...

    public String toString() {
        return this.name + ", age " + this.age + " years";
    }
}
```

The `toString` method in Java returns a string representation of an object, whereas the `printPerson` method prints the object directly to the console. By separating the generation of a string representation from its use, we can create more flexible and reusable code.

The method is used in a somewhat surprising way:

```java
public static void main(String[] args) {
    Person pekka = new Person("Pekka");
    Person antti = new Person("Antti");

    int i = 0;
    while (i < 30) {
        pekka.growOlder();
        i = i + 1;
    }

    antti.growOlder();

    System.out.println(antti); // same as System.out.println(antti.toString());
    System.out.println(pekka); // same as System.out.println(pekka.toString());
}
```

In Java, the `System.out.println` method can be used to print an object's string representation. When this method is called on an object, Java automatically calls the object's `toString` method to generate the string representation.

As a result, programmers do not have to explicitly call the `toString` method when using `System.out.println` to print an object. When a programmer writes:

```java
System.out.println(antti);
```

Java extends the call at run time to the following form:

```java
System.out.println(antti.toString());
```

As such, the call `System.out.println(antti)` calls the `toString` method of the `antti` object and prints the string returned by it.
This implies that we can remove the now obsolete `printPerson` method from the `Person` class.


<programming-exercise name='Agent'>

The exercise template defines an Agent class, having a first name and last name. A `print` method is defined for the class that creates the following string representation.

```java
Agent bond = new Agent("James", "Bond");
bond.print();
```

<sample-output>

My name is Bond, James Bond

</sample-output>

Remove the class' `print` method, and create a `public String toString()` method for it, which returns the string representation shown above.

The class should function as follows.

```java
Agent bond = new Agent("James", "Bond");

bond.toString(); // prints nothing
System.out.println(bond);

Agent ionic = new Agent("Ionic", "Bond");
System.out.println(ionic);
```

<sample-output>

My name is Bond, James Bond
My name is Bond, Ionic Bond

</sample-output>

</programming-exercise>

## Method parameters
Let's continue with the `Person` class once more. We've decided that we want to calculate people's body mass indexes. To do this, we write methods for the person to set both the height and the weight, and also a method to calculate the body mass index. The new and changed parts of the Person object are as follows:

```java
public class Person {
    private String name;
    private int age;
    private int weight;
    private int height;

    public Person(String initialName) {
        this.age = 0;
        this.weight = 0;
        this.height = 0;
        this.name = initialName;
    }

    public void setHeight(int newHeight) {
        this.height = newHeight;
    }

    public void setWeight(int newWeight) {
        this.weight = newWeight;
    }

    public double bodyMassIndex() {
        double heigthPerHundred = this.height / 100.0;
        return this.weight / (heigthPerHundred * heigthPerHundred);
    }

    // ...
}
```

The instance variables `height` and `weight` were added to the person. Values for these can be set using the `setHeight` and `setWeight` methods. Java's standard naming convention is used once again, that is, if the method's only purpose is to set a value to an instance variable, then it's named as `setVariableName`. Value-setting methods are often called "setters". The new methods are put to use in the following case:

```java
public static void main(String[] args) {
    Person matti = new Person("Matti");
    Person juhana = new Person("Juhana");

    matti.setHeight(180);
    matti.setWeight(86);

    juhana.setHeight(175);
    juhana.setWeight(64);

    System.out.println(matti.getName() + ", body mass index is " + matti.bodyMassIndex());
    System.out.println(juhana.getName() + ", body mass index is " + juhana.bodyMassIndex());
}
```

Prints:

<sample-output>

Matti, body mass index is 26.54320987654321
Juhana, body mass index is 20.897959183673468

</sample-output>

## A parameter and instance variable having the same name!
In the preceding example, the `setHeight` method sets the value of the parameter `newHeight` to the instance variable `height`:

```java
public void setHeight(int newHeight) {
    this.height = newHeight;
}
```

The parameter's name could also be the same as the instance variable's, so the following would also work:

```java
public void setHeight(int height) {
    this.height = height;
}
```

In this case, `height` in the method refers specifically to a parameter named _height_ and `this.height` to an instance variable of the same name. For example, the following example would not work as the code does not refer to the instance variable _height_ at all. What the code does in effect is that it sets the `height` variable received as a parameter to the value it already contains:

```java
public void setHeight(int height) {
    // DO NOT DO THIS!!!
    height = height;
}
```

```java
public void setHeight(int height) {
    // DO THIS INSTEAD!!!
    this.height = height;
}
```

<programming-exercise name='Multiplier'>

Create a class Multiplier that has a:

- Constructor `public Multiplier(int number)`.
- Method `public int multiply(int number)` which returns the value `number` passed to it multiplied by the `number` provided to the constructor.

You also need to create an instance variable in this exercise.

An example of the class in use:

```java
Multiplier multiplyByThree = new Multiplier(3);

System.out.println("multiplyByThree.multiply(2): " + multiplyByThree.multiply(2));

Multiplier multiplyByFour = new Multiplier(4);

System.out.println("multiplyByFour.multiply(2): " + multiplyByFour.multiply(2));
System.out.println("multiplyByThree.multiply(1): " + multiplyByThree.multiply(1));
System.out.println("multiplyByFour.multiply(1): " + multiplyByFour.multiply(1));
```

Output

<sample-output>

multiplyByThree.multiply(2): 6
multiplyByFour.multiply(2): 8
multiplyByThree.multiply(1): 3
multiplyByFour.multiply(1): 4

</sample-output>

</programming-exercise>

## Calling an internal method
The object can also invoke its own methods. For instance, if we wished to include a person's body mass index in the string representation returned by `toString`, we would need to call the object's `bodyMassIndex` method from within the `toString` method:

```java
public String toString() {
    return this.name + ", age " + this.age + " years, my body mass index is " + this.bodyMassIndex();
}
```

When an object calls an internal method, it is enough to use the method name and "this" prefix. Another way to call the object's own method is to use the method name directly, i.e., `bodyMassIndex()`. Both ways are valid, but the former makes it clearer that the method being called is an internal method of the object.

```java
public String toString() {
    return this.name + ", age " + this.age + " years, my body mass index is " + bodyMassIndex();
}
```


## Video
In the following video, we show how a class can be implemented from scratch.

<panopto src="https://eur.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=5cb642bd-b2c1-4770-a00a-acf20112d694&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all"></panopto>

<programming-exercise name='Statistics (4 parts)'>

<h2>Count</h2>

Create a class `Statistics` that has the following functionality (the file for the class is provided in the exercise template):

- a method `addNumber` adds a new number to the statistics
- a method `getCount` tells the number of added numbers

The class does not need to store the added numbers anywhere, it is enough for it to remember their count. At this stage, the `addNumber` method can even neglect the numbers being added to the statistics, since the only thing being stored is the count of numbers added.

The method's body is the following:

```java
public class Statistics {
    private int count;

    public Statistics() {
        // initialize the variable numberCount here
    }

    public void addNumber(int number) {
        // write code here
    }

    public int getCount() {
        // write code here
    }
}
```

The following program introduces the class' use:

```java
public class MainProgram {
    public static void main(String[] args) {
        Statistics statistics = new Statistics();
        statistics.addNumber(3);
        statistics.addNumber(5);
        statistics.addNumber(1);
        statistics.addNumber(2);
        System.out.println("Count: " + statistics.getCount());
    }
}
```

The program prints the following:

<sample-output>

Count: 4

</sample-output>

<h2>Sum and average</h2>

Expand the class with the following functionality:

- the `sum` method tells the sum of the numbers added (the sum of an empty number statistics object is 0)
- the `average` method tells the average of the numbers added (the average of an empty number statistics object is 0

The class' template is the following:

```java
public class Statistics {
    private int count;
    private int sum;

    public Statistics() {
        // initialize the variables count and sum here
    }

    public void addNumber(int number) {
        // write code here
    }

    public int getCount() {
        // write code here
    }

    public int sum() {
        // write code here
    }

    public double average() {
        // write code here
    }
}
```

The following program demonstrates the class' use:

```java
public class Main {
    public static void main(String[] args) {
        Statistics statistics = new Statistics();
        statistics.addNumber(3);
        statistics.addNumber(5);
        statistics.addNumber(1);
        statistics.addNumber(2);
        System.out.println("Count: " + statistics.getCount());
        System.out.println("Sum: " + statistics.sum());
        System.out.println("Average: " + statistics.average());
    }
}
```

The program prints the following:

<sample-output>

Count: 4
Sum: 11
Average: 2.75

</sample-output>

<h2>Sum of user input</h2>

Write a program that asks the user for numbers until the user enters -1. The program will then provide the sum of the numbers.

The program should use a `Statistics` object to calculate the sum.

**NOTE:** Do not modify the Statistics class in this part. Instead, implement the program for calculating the sum by making use of it.

<sample-output>

Enter numbers:
**4**
**2**
**5**
**4**
**-1**
Sum: 15

</sample-output>

</programming-exercise>

<text-box variant='hint' name='Rounding errors'>

You probably noticed that some of the figures have rounding errors. In the previous exercise, for example, Pekka's balance of 30.7 may be printed as `30.700000000000003`. This is because floating-point numbers, such as `double`, are actually stored in binary form. That is, in zeros and ones using only a limited number of numbers.
As the number of floating-point numbers is infinite -- (in case you're wondering "how infinite?", think how many floating-point or decimal values fit between the numbers 5 and 6 for instance). All of the floating-point numbers simply cannot be represented by a finite number of zeros and ones. Thus, the computer must place a limit on the accuracy of stored numbers.

Normally, account balances, for instance, are saved as integers such that, say, the value 1 represents one cent.

</text-box>
