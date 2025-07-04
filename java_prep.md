# Java Programming Guide

## Table of Contents
1. [Introduction](#introduction)
2. [Java Development Environment](#java-development-environment)
3. [Basic Syntax](#basic-syntax)
4. [String Operations](#string-operations)
5. [Operators](#operators)
6. [Control Flow](#control-flow)
7. [Arrays](#arrays)
8. [Object-Oriented Programming](#object-oriented-programming)
9. [Multithreading](#multithreading)

## Introduction

Java is known for its **"Write once, Run Anywhere"** capability, meaning Java code can run on any platform that has a Java Virtual Machine (JVM) installed. This platform independence is one of Java's biggest strengths.

## Java Development Environment

### Installation
**Install Java = Install JDK**

When you install JDK, you are also installing JVM and JRE.

### Components Overview

```
JDK
├── Development Tools (javac)
├── Source code 
└── JRE
    ├── JVM
    ├── Core Classes (compiled)
    └── Supporting files
```

#### JDK (Java Development Kit)
A comprehensive software development environment used for developing Java Applications. It includes:
1. The Java compiler (javac) to convert Java source code (.java files) into bytecodes (.class files)
2. Development tools like debuggers, documentation generator (javadoc)
3. Source files for Java core classes
4. The JRE (which includes the JVM)

#### JRE (Java Runtime Environment)
What's needed to run Java applications on a computer. It consists of:
1. The Java Virtual Machine (JVM)
2. Compiled Core classes (like String, Integer, ArrayList, etc.) and supporting files
3. Configuration files that tell Java how to run
4. **No development tools** (unlike JDK) - meant for end users who just want to run Java applications

#### Summary
- **JDK** contains **JRE** which contains **JVM**
- **Developers** need **JDK** to create Java applications
- **JVM** is the actual engine that runs the Java Bytecode on any platform

## Basic Syntax

### Hello World Program
```java
class Test {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

**Explanation:**
- **System**: A class in java.lang package that provides access to the system, including console
- **out**: An instance of the PrintStream class within the System class, representing the console
- **println**: A method used to print a line of text to the console

### String Immutability
```java
class Test {
    public static void main(String[] args) {
        String a = "hello";
        a = a.toUpperCase(); // Must reassign to see changes due to immutability
        System.out.println(a); // Output: HELLO
    }
}
```

## String Operations

```java
public class Test {
    public static void main(String[] args) {
        String str = "Hello, World!";

        // Length of the string
        System.out.println(str.length()); // 13

        // Accessing characters in the string
        System.out.println(str.charAt(0)); // H

        // Substring from index 0 to 5
        System.out.println(str.substring(0, 5)); // Hello

        // Contains, startsWith, endsWith
        System.out.println(str.contains("World")); // true

        // Replace
        System.out.println(str.replace("World", "Java")); // Hello, Java!
    }
}
```

## Operators

### Arithmetic Operators
- **Left shift** `<< 2` → multiply by 2
- **Right shift** `>> 2` → divide by 2

### Logical Operators
Used to combine multiple boolean expressions:
- **AND** → `&&`
- **OR** → `||`
- **NOT** → `!`

## Control Flow

### Conditionals
```java
public class Test {
    public static void main(String[] args) {
        boolean isSunny = true;
        boolean isWarm = false;

        if (isSunny && isWarm) {
            System.out.println("Beach Day");
        } else if (isSunny) {
            System.out.println("Wear jacket");
        } else {
            System.out.println("Stay home");
        }
    }
}
```

### Switch Statement
```java
public class Test {
    public static void main(String[] args) {
        int day = 3;
        String dayName = "";

        switch (day) {
            case 1: dayName = "Monday"; break;
            case 2: dayName = "Tuesday"; break;
            case 3: dayName = "Wednesday"; break;
            case 4: dayName = "Thursday"; break;
            case 5: dayName = "Friday"; break;
            case 6: dayName = "Saturday"; break;
            case 7: dayName = "Sunday"; break;
            default: dayName = "Invalid day";
        }
        System.out.println("Day is " + dayName);
    }
}
```

### Ternary Operator
```java
public class Test {
    public static void main(String[] args) {
        // result = (condition) ? valueIfTrue : valueIfFalse;
        int a = 5;
        String res = (a % 2 == 0) ? "even" : "odd";
        System.out.println("The number is: " + res);
    }
}
```

### Loops

#### While Loop
```java
public class Test {
    public static void main(String[] args) {
        int i = 1;
        while (i <= 100) {
            System.out.println(i);
            i++;
        }
    }
}
```

#### For Loop
```java
public class Test {
    public static void main(String[] args) {
        for (int i = 0; i <= 100; i++) {
            System.out.println("Hello World " + i);
        }
    }
}
```

#### Do-While Loop
```java
public class Test {
    public static void main(String[] args) {
        int i = 1;
        do {
            System.out.println(i);
            i++;
        } while (i <= 100);
    }
}
```

## Arrays

An array in Java is a data structure that stores a fixed-size sequential collection of elements of the same type.

### Declaration and Creation
```java
// Declaration
int[] a;  // recommended
// OR
int a[]; // allowed but less used

// Initialization
int[] a = {1, 3, 4, 5, 3};

// Creation with new keyword
int[] a = new int[5]; // creates an array of zeroes
a[4] = 55;

// Accessing elements
for (int i = 0; i < 5; i++) {
    System.out.println(a[i]);
}

// Enhanced for loop (for-each)
for (int element : a) {
    System.out.println(element);
}
```

## Object-Oriented Programming

A programming paradigm that uses objects and classes to design and implement software solutions.

### Key Concepts
1. **Class** - Blueprint for creating objects
2. **Object** - Instance of a class
3. **Encapsulation** - Bundling data and methods together
4. **Inheritance** - Acquiring properties from another class
5. **Polymorphism** - Methods performing different tasks based on the object
6. **Abstraction** - Hiding implementation details

### The Four Pillars of OOP

#### 1. Encapsulation
Bundling data (fields) and methods that operate on the data into a single unit (class), with restricted access using access modifiers.

#### 2. Inheritance
Allows a class to acquire properties and methods of another class, supporting code reusability.

**Types:**
- Single
- Multilevel
- Hierarchical

**Note:** Java does not support Multiple Inheritance directly.

#### 3. Polymorphism
Allows methods to perform different tasks based on the object that calls them.

##### Method Overloading (Compile-Time Polymorphism)
```java
class Calculator {
    // Add two numbers
    int add(int a, int b) {
        return a + b;
    }

    // Add three numbers
    int add(int a, int b, int c) {
        return a + b + c;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(1, 2));    // Output: 3
        System.out.println(calc.add(1, 2, 3)); // Output: 6
    }
}
```

##### Method Overriding (Runtime Polymorphism)
```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal1 = new Dog();
        Animal animal2 = new Cat();
        animal1.sound(); // Output: Dog barks
        animal2.sound(); // Output: Cat meows
    }
}
```

#### 4. Abstraction
Focuses on showing only essential details while hiding implementation. Achieved through abstract classes and interfaces.

##### Abstract Class
```java
abstract class Animal {
    abstract void sayHello();
    abstract void sayGoodbye();

    void sleep() {
        System.out.println("Animal is sleeping");
    }
}

class Dog extends Animal {
    @Override
    void sayHello() {
        System.out.println("Dog says: Woof Woof");
    }

    @Override
    void sayGoodbye() {
        System.out.println("Dog says: Goodbye");
    }
}
```

##### Interface
```java
interface Mobile {
    void makeCall();
    int battery = 5400; // By default public, static, and final
}

interface MusicPlayer {
    void playMusic();
}

class SmartPhone implements Mobile, MusicPlayer {
    @Override
    public void makeCall() {
        System.out.println("Making call....");
    }

    @Override
    public void playMusic() {
        System.out.println("Playing Music....");
    }
}
```

**Interface Features:**
- Achieves abstraction and multiple inheritance
- Can have abstract methods, static constants, static methods, and default methods

##### Static Methods in Interface
```java
interface PaymentValidator {
    boolean validatePayment(Payment payment);

    // Static utility methods
    static boolean isValidCreditCard(String cardNumber) {
        return cardNumber.length() == 16;
    }

    static boolean isValidAmount(double amount) {
        return amount > 0 && amount < 1000000;
    }
}
```

##### Default Methods in Interface
```java
interface PaymentProcessor {
    void processPayment(Payment payment);

    // Default method using abstract method
    default void processPayments(List<Payment> payments) {
        for (Payment payment : payments) {
            processPayment(payment);
        }
    }

    // Default method with common implementation
    default void validateAndProcess(Payment payment) {
        if (payment.getAmount() <= 0) {
            throw new IllegalArgumentException("Invalid amount");
        }
        processPayment(payment);
    }
}
```

### Interface vs Abstract Class

| Interface | Abstract Class |
|-----------|----------------|
| Only static fields (public, static, final by default) | Normal and static fields allowed |
| No constructors | Can have constructors |
| Supports multiple inheritance | No multiple inheritance |
| Blueprint for classes | Blueprint for objects |

## Multithreading

### Key Concepts

#### CPU and Cores
- **CPU**: The brain of the computer, responsible for executing instructions
- **Core**: Individual processing unit within a CPU; modern CPUs have multiple cores

#### Program vs Process vs Thread
- **Program**: Set of instructions (e.g., Microsoft Word)
- **Process**: Instance of a program being executed
- **Thread**: Smallest unit of execution within a process

### Multitasking vs Multithreading

#### Multitasking
- Allows OS to run multiple processes simultaneously
- Single-core: Rapid switching between tasks
- Multi-core: True parallel execution across cores

#### Multithreading
- Concurrent execution of multiple threads within a single process
- Example: Web browser using separate threads for rendering, JavaScript, and user input

### Java Multithreading

Java supports multithreading through:
- `java.lang.Thread` class
- `java.lang.Runnable` interface

**Key Points:**
- Every Java program starts with a **Main Thread**
- Threads can be created by extending `Thread` class or implementing `Runnable` interface
- In single-core: JVM uses time-slicing for thread management
- In multi-core: True parallel execution across cores

### Thread Creation Methods

1. **Extending Thread class**
2. **Implementing Runnable interface**

---

## Contributing
Feel free to contribute to this guide by adding more examples, explanations, or corrections.

## License
This guide is for educational purposes.
