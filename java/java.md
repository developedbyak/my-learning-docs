# Java

Java is a widely-used programming language that is designed to be platform-independent, meaning it can run on any device or operating system. It was first released in 1995 and has since become one of the most popular programming languages in the world. Java is known for its simplicity, reliability, and security features. It is commonly used for developing various types of applications, including web and mobile applications, enterprise software, and embedded systems.

> Click ⭐ if you like the project and follow [@developedbyak](https://twitter.com/developedbyak) for more updates.

### Table of Contents

| No. | Topics                                                                 |
| --- | ---------------------------------------------------------------------- |
| 1   | [Install Java](#1-install-java)                                        |
| 2   | [Sample Code](#2-sample-code)                                          |
| 3   | [Our First Program](#3-our-first-program)                              |
| 4   | [Variables](#4-variables)                                              |
| 5   | [Data Types](#5-data-types)                                            |
| 6   | [String Class](#6-string-class)                                        |
| 7   | [Arrays](#7-arrays)                                                    |
| 8   | [Casting](#8-casting)                                                  |
| 9   | [Constants](#9-constants)                                              |
| 10  | [Operators](#10-operators)                                             |
| 11  | [Math class](#11--math-class)                                          |
| 12  | [Taking Input](#12-taking-input)                                       |
| 13  | [Conditional Statements ‘if-else’](#13-conditional-statements-if-else) |
| 14  | [Conditional Statement ‘switch’](#14-conditional-statement-switch)     |
| 15  | [Break & Continue](#15-break--continue)                                |
| 16  | [Loops](#16-loops)                                                     |
| 17  | [Exception Handling (try-catch)](#17-exception-handling-try-catch)     |
| 18  | [Types of Exceptions](#18-types-of-exceptions-and-there-use)           |
| 19  | [Methods / Functions](#19-methods--functions)                          |
| 20  | [Mini-Project](#20-mini-project)                                       |

### 1. Install Java

-   Install JDK ([Java Downloads | Oracle India](https://www.oracle.com/in/java/technologies/downloads/))
-   Install IntelliJ ([Download IntelliJ IDEA – The Leading Java and Kotlin IDE (jetbrains.com)](https://www.jetbrains.com/idea/download/?section=windows#section=mac))

### 2. Sample Code

**Functions**

A function is a block of code which takes some input, performs some operations
and returns some output.
The functions stored inside classes are called methods.
The function we have used is called main.

**Class**

A class is a group of objects which have common properties. A class can have
some properties and functions (called methods).
The class we have used is Main.

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 3. Our First Program

```java
public class Main {
	public static void main(String[] args) {
		System.out.print("Hello World");
	}
}

// output
Hello World
```

What if we want out output in next line ?

What is the use of ln or \n ?
For example :

```java
// 1st type
public class Main {
	public static void main(String[] args) {
		System.out.print("I love");
		System.out.print("java");
	}
}

// 2nd type
public class Main {
	public static void main(String[] args) {
		System.out.println("I love");
		System.out.print("java");
	}
}

// 3rd type
public class Main {
	public static void main(String[] args) {
		System.out.print("I love\njava");
	}
}

// 1st output
I lovejava
// 2nd output
I love
java
// 3rd output
I love
java
```

### 4. Variables

A variable is a container (storage area) used to hold data.
Each variable should be given a unique name (identifier).

```java
// Variables
String name = "Akash";
int age = 24;
String friendName = "meow";
boolean bestfriends = true;
Boolean isNull = null;
int year = 2023;
double temp = 22.4;
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 5. Data Types

Data types are declarations for variables. This determines the type and size of
data associated with variables which is essential to know since different data
types occupy different sizes of memory.

There are 2 types of Data Types :

-   **Primitive Data types** : to store simple values
-   **Non-Primitive Data types** : to store complex values

**Primitive Data Types**
These are the date types of fixed size.

| Data Type | Meaning                               | Size (in Bytes) | Range                                                  |
| --------- | ------------------------------------- | --------------- | ------------------------------------------------------ |
| byte      | 2’s complement integer                | 1               | -128 to 127                                            |
| short     | 2’s complement integer                | 2               | -32k to 32k                                            |
| int       | integer numbers                       | 4               | -2B to 2B                                              |
| long      | 2’s complement integer (large values) | 8               | -9,223,372,036854,775,808 to 9,223,372,036,854,775,807 |
| float     | Floating-point                        | 4               | Upto 7 decimal digits                                  |
| double    | Double Floating-point                 | 8               | Upto 16 decimal digits                                 |
| char      | Character                             | 2               | a,b,c… A,B,C… @,#,$…                                   |
| bool      | Boolean                               | 1               | True, False                                            |

**Non-Primitive Data Types**
These are of variable size & are usually declared with a ‘new’ keyword.

Eg : String, Arrays, Class, Object, Interface

```java
String name = new String ("Aman");
String name1 = "Akash"

int[] marks = {98, 97, 93};
System.out.println(Arrays.toString(marks));
int[] marks = new int[3];
marks[0] = 97;
marks[1] = 98;
marks[2] = 95;
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 6. String Class

Strings are immutable non-primitive data types in Java. Once a string is created
it’s value cannot be changed i.e. if we wish to alter its value then a new string
with a new value has to be created.
This class in java has various important methods that can be used for Java
objects. These include:

```java
// using 'new' keyword
String name1 = new String("Akash");
String description = new String("is a good boy.");

// using string literals
String name1 = "Akash"
String description = "is a good boy."

// Concatenation
        String sentence = name1 + description;
        System.out.println(sentence); // Akash is a good boy.
        // charAt
        System.out.println(sentence.charAt(0)); // A
        // Length
        System.out.println(sentence.length()); // 20
        // Replace
        System.out.println(sentence.replace("A", "B")); // Bkash is a good boy.
        // Substring
        System.out.println(sentence.substring(0,4)); // Akas
```

### 7. Arrays

Arrays in Java are like a list of elements of the same type i.e. a list of integers, a
list of booleans etc.

```java
import java.util.Arrays;

// Creating an Array (method 1) - with new keyword
int[] marks = new int[3];
marks[0] = 98;
marks[1] = 97;
marks[2] = 95;

// Array Initialization with Values: (method 2)
int[] marks = {98, 97, 93};
String[] names = {"Akash", "Lee", "Meow"};

System.out.println(Arrays.toString(names)); // [Akash,Lee,Meow]

```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 8. Casting

Casting in java is the assigning values of one type to another. The types being
considered here are compatible i.e. we can only assign values of a number type
to another type storing numbers (vice-versa is not allowed i.e. floating values
cannot be assigned to boolean data types).
Casting in Java is of 2 types:

1. Implicit casting
   This casting is done by java implicitly i.e. on its own. It is assigning smaller
   values to larger data types.

```java
float price = 100.00F;
int gst = 18;
float finalPrice = price + gst;
```

1. Explicit casting
   This casting is done by the programmer. It is assigning larger values to smaller
   data types.

```java
int price = 100;
float gst = 18.00F;
int finalPrice = price + (int)gst;
```

### 9. Constants

A constant is a variable in Java which has a fixed value i.e. it cannot be assigned a different value
once assigned.

```java
public class Main {
	public static void main(String[] args) {
		// Constants
		final float PI = 3.14F;
}
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 10. Operators

There are 4 types of operators in java:
<br>

<h2>Arithmetic Operators</h2>
    Arithmetic operators are just like operators we used in Math.
    These include:

<br>

```java
int a = 60;
int b = 10;

// '+' Add
int sum = a + b;

// '-' Subtract
int diff = a - b;

// '*' Multiply
int mul = a * b;

// '/' Divide
int div = a / b;

// '%' Modulo - Remainder of a/b
int rem = a % b;

// Unary Operators (increment and decrement in javascript)

a++; // post-increment
a--; // post-decrement
++a; // pre-increment
--a; // pre-decrement
```

-   Pre-increment: It increments the value of the operand instantly;

-   Post-increment: It stores the current value of the operand temporarily and only after that statement is completed, the value of the operand is incremented.

-   Pre-decrementer: It decrements the value of the operand
    instantly.

-   Post-decrementer: It stores the current value of the operand
    temporarily and only after that statement is completed, the value
    of the operand is decremented.

<br>

<h2>Assignment Operators</h2>

<br>

| Operator       | Operation                                                                                      | Example                      |
| -------------- | ---------------------------------------------------------------------------------------------- | ---------------------------- |
| = ( equality ) | Assigns value of right operand to left operand                                                 | A=B will put value of B in A |
| +=             | Adds right operand to the left operand and assigns the result to left operand.                 | A+=B means A = A+B           |
| -=             | Subtracts right operand from the left operand and assigns the result to left operand.          | A-=B means A = A-B           |
| \*=            | Multiplies the right operand with the left operand and assigns the result to the left operand. | A*=B means A = A*B           |
| /=             | Divides left operand with the right operand and assigns the result to left operand.            | A/=B means A = A/B           |

<br>

<h2>Comparison/Relational Operators</h2>
   Relational operators define the relation between 2 entities.
   They give a boolean value as a result i.e. true or false

<br>

**Suppose : A = 5 and B = 10**

| Operators | Operations                                                           | Example          |
| --------- | -------------------------------------------------------------------- | ---------------- |
| ==        | Gives true if two operands are equal                                 | A == B ( false ) |
| !=        | Gives true if two operands are not equal                             | A == B ( true )  |
| >         | Gives true if left operand is more than right operand                | A > B ( false )  |
| <         | Gives true if left operand is less than right operand                | A < B ( true )   |
| >=        | Gives true if left operand is more than right operand or equal to it | A >= B ( false ) |
| <=        | Gives true if left operand is more than right operand or equal to it | A <= B ( true )  |

<br>

<h2>Logical Operators</h2>

<br>

Logical operators are used to connect multiple expressions or conditions
together. <br>
We have 3 basic logical operators <br>
**Suppose : A = 0 and B = 1**

| Operators | Operations                                                               | Example           |
| --------- | ------------------------------------------------------------------------ | ----------------- |
| &&        | AND operator. Gives true if both operands are non zero                   | (A && B) is false |
| II        | OR operator. Gives true if atleast one of the two operands are non-zero. | (A II B) is true  |
| !         | NOT operator. Reverse the logical state of operand                       | !A is true        |

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 11 . Math class

Math is an important class in Java that is extensively used and has a lot of
interesting functions.

```java
// To import
import java.lang.Math;

int a = 10;
int b = 20;
// Some functions include:
//Max
Math.max(a,b);
//Min
Math.min(a,b);
//Random
int randomNumber =  (int) (Math.random()*10);
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 12. Taking Input

We take input using the Scanner class and input various types of data using it .

```java
// To import Scanner class
import java.util.Scanner;

// Example
Scanner sc = new Scanner(Syatem.in);

System.out.print("Enter an integer: ");
int n = sc.nextInt();
System.out.print("Enter a float value: ");
float a = sc.nextFloat();
System.out.print("Enter a name: ");
String name = sc.next();
System.out.print("Enter a line: ");
sc.nextLine(); // to clean the input buffer
String line = sc.nextLine();

System.out.println(n + "\n" + name + "\n" + line);
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 13. Conditional Statements ‘if-else’

The if block is used to specify the code to be executed if the condition specified
in if is true, the else block is executed otherwise.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your age: ");
        int age = sc.nextInt();
        if (age > 18) {
            System.out.println("You are an adult");
        } else {
            System.out.println("You are not an adult");
        }
    }
}
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 14. Conditional Statement ‘switch’

Switch case statements are a substitute for long if statements that compare a
variable to multiple values. After a match is found, it executes the
corresponding code of that value case.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int day;

        System.out.print("Enter code for day: ");
        day = sc.nextInt();
        if (day > 7) {
            System.out.println("Wrong code for the day");
            return;
        }
        switch (day) {
            case 1:
                System.out.println("Monday");
                break;
            case 2:
                System.out.println("Tuesday");
                break;
            case 3:
                System.out.println("Wednesday");
                break;
            case 4:
                System.out.println("Thursday");
                break;
            case 5:
                System.out.println("Friday");
                break;
            case 6:
                System.out.println("Saturday");
                break;
            default:
                System.out.println("Sunday");
        }
    }
}
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 15. Break & Continue

Jumps in loops are used to control the flow of loops.<br>
There are two statements used to implement jump in loops - **Continue and Break**.

These statements are used when we need to change the **flow of the loop** when some specified condition is met.

**Continue statement** is used to skip to the next iteration of that loop. This
means that it stops one iteration of the loop. All the statements present after
the continue statement in that loop are not executed.

```java
public class Main {
    public static void main(String[] args) {
        int i;
        for (i = 0; i<20; i++) {
            if (i%3 == 0) {
                continue;
            }
            System.out.println(i);
        }
    }
}
```

In this for loop, whenever i is a number divisible by 3, it will not be printed as the
loop will skip to the next iteration due to the continue statement. Hence, all the
numbers except those which are divisible by 3 will be printed.

**Break statement** is used to terminate the current loop. As soon as the break
statement is encountered in a loop, all further iterations of the loop are stopped
and control is shifted to the first statement after the end of loop.

```java
public class Main {
    public static void main(String[] args) {
        int i;
        for (i = 0; i<20; i++) {
            if (i == 11) {
                break;
            }
            System.out.println(i);
        }
    }
}
```

In this loop, when i becomes equal to 11, the for loop terminates due to break
statement, Hence, the program will print numbers from 1 to 10 only.

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 16. Loops

A loop is used for executing a block of statements repeatedly until a particular
condition is satisfied. A loop consists of an initialization statement, a test
condition and an increment statement.

In Java, there are three main types of loops:

<h3>for loop </h3> 
This loop is used when you know how many times you want to repeat a block of code. It has three parts: initialization, condition, and iteration.

<br>

```java
// for loop syntax
for (initialization; condition; iteration) {
	// your logic
}

// Example
public class Main {
    public static void main(String[] args) {
        int i;
        for (i = 0; i<=5; i++) {
            System.out.println(i);
        }
    }
}
```

<h3>while loop</h3>
This loop is used when you want to repeat a block of code as long as a certain condition is true.

<br>

```java
// while loop syntax
while (condition) {
	// your code

	// iteraion
}

// Example
public class Main {
    public static void main(String[] args) {
        int i = 0;
        while (i < 5) {
            // your code to run
            System.out.println(i);

            // iteration
            i++;
        }
    }
}
```

<h3>Do-While Loop</h3> 
This loop is similar to the **`while`** loop but guarantees that the block of code is executed at least once, even if the condition is initially false.

<br>

```java
// do-while loop syntax
do {
	// your code to run
	// iteration
} while (condition);

// Example
public class Main {
    public static void main(String[] args) {
        int i = 0;
        do {
            System.out.println("i will run no matter what !");
            i++;
        } while (i > 5);
    }
}
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 17. Exception Handling (try-catch)

Exception Handling in Java is a mechanism to handle the runtime errors so that
normal flow of the application can be maintained.

It is done using 2 keywords - `try` and `catch`.

Additional keywords like finally, throw and throws can also be used if we dive
deep into this concept.

**try block:** Inside the **`try`** block, you place the code that might throw an exception. If an exception occurs within the **`try`** block, the normal flow of the program is interrupted.

```java
// Example
try {
    int result = 10 / 0; // This will throw an ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("An exception occurred: " + e.getMessage());
} finally {
    System.out.println("Finally block always executes.");
}
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 18. Types of Exceptions and there use.

In Java, exceptions are categorized into **two main types**:

1. **Checked Exceptions (Compile-Time Exception):**

These are exceptions that the Java compiler checks at compile time. They are exceptions that a method is required to declare in its throws clause if it can throw them. They include exceptions that are typically beyond the control of the program, such as file I/O errors, network connectivity issues, or database errors. Some common checked exceptions include:

-   **IOException** : This is a superclass for various exceptions related to input and output operations.
-   **SQLException** : This is used for handling exceptions related to database operations.
-   **FileNotFoundException** : Thrown when a file being read or written to is not found.

1. **Unchecked Exceptions (Runtime Exceptions):**

These are exceptions that the Java compiler does not require you to catch or declare. They can occur at runtime and are typically caused by programming errors. They often represent situations where the program can't proceed due to a logical issue. Some common unchecked exceptions include:

-   **NullPointerException :** Occurs when you try to access a method or field on an object that is **null**.
-   **ArithmeticException :** Occurs when an arithmetic operation (e.g., division by zero) is not valid.
-   **ArrayIndexOutOfBoundsException :** Occurs when trying to access an array element with an invalid index.
-   **ClassCastException :** Occurs when trying to cast an object to an incompatible type.

**Examples :**

```java
import java.io.IOException;

public class CheckedExceptionExample {
    public static void main(String[] args) {
        try {
            throw new IOException("This is an IOException");
        } catch (IOException e) {
            System.out.println("Caught an IOException: " + e.getMessage());
        }
    }
}
```

```java
import java.sql.SQLException;

public class CheckedExceptionExample {
    public static void main(String[] args) {
        try {
            throw new SQLException("This is an SQLException");
        } catch (SQLException e) {
            System.out.println("Caught an SQLException: " + e.getMessage());
        }
    }
}
```

```java
import java.io.FileNotFoundException;

public class CheckedExceptionExample {
    public static void main(String[] args) {
        try {
            throw new FileNotFoundException("This is a FileNotFoundException");
        } catch (FileNotFoundException e) {
            System.out.println("Caught a FileNotFoundException: " + e.getMessage());
        }
    }
}
```

```java
public class UncheckedExceptionExample {
    public static void main(String[] args) {
        try {
            String str = null;
            System.out.println(str.length()); // This will throw a NullPointerException
        } catch (NullPointerException e) {
            System.out.println("Caught a NullPointerException: " + e.getMessage());
        }
    }
}
```

```java
public class UncheckedExceptionExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0; // This will throw an ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Caught an ArithmeticException: " + e.getMessage());
        }
    }
}
```

```java
public class UncheckedExceptionExample {
    public static void main(String[] args) {
        try {
            int[] arr = {1, 2, 3};
            int value = arr[5]; // This will throw an ArrayIndexOutOfBoundsException
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Caught an Error: " + e.getMessage());
        }
    }
}
```

```java
public class UncheckedExceptionExample {
    public static void main(String[] args) {
        try {
            Object obj = "Hello";
            Integer num = (Integer) obj; // This will throw a ClassCastException
        } catch (ClassCastException e) {
            System.out.println("Caught a ClassCastException: " + e.getMessage());
        }
    }
}
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 19. Methods / Functions

A function is a block of code that performs a specific task.
**Why are functions used?**

-   If some functionality is performed at multiple places in software, then
    rather than writing the same code, again and again, we create a function
    and call it everywhere. This helps reduce code redundancy.
-   Functions make maintenance of code easy as we have to change at one
    place if we make future changes to the functionality.
-   Functions make the code more readable and easy to understand.

The **syntax** for function declaration is :

```java
return-type function_name(parameter1, parameter2,...) {
	// logic
}
return-type
```

-   The **return type** of a function is the data type of the variable that that function
    returns.
-   For eg- If we write a function that adds 2 integers and returns their sum then
    the return type of this function will be ‘int’ as we will return a sum that is an
    integer value.
-   When a function does not return any value, in that case the return type of the
    function is ‘void’.

**function_name -**

-   It is the unique name of that function.
-   It is always recommended to declare a function before it is used.
    Parameters.
-   A function can take some parameters as inputs. These parameters are specified
    along with their data types.
-   For eg- if we are writing a function to add 2 integers, the parameters would be
    passed like –
    int add (int num1, int num2)

**main function -**
The main function is a special function as the computer starts running the code
from the beginning of the main function. Main function serves as the entry point
for the program.
Example :

```java
public class Main {

		// function
    public static int mul(int a, int b) {
        return a*b;
    }

    public static void main(String[] args) {
        int a = 5;
        int b = 10;
        int res = mul(a,b); // call function and get data
        System.out.println(res);
    }
}

OR

public class Main {

    public static void mul(int a, int b) {
        int mul = a*b;
				System.out.println(mul); // here the function is not returning anything.
    }

    public static void main(String[] args) {
        int a = 5;
        int b = 10;
        mul(a,b); // function call
    }
}
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>

### 20. Mini-Project

<h3>Let’s create a project where we are trying to ask the user to guess a randomly
generated number.</h3>

<br>

-   The number is in the range of 1 to 100.
-   If the user guesses a number that is greater, we print “The number is too large”.
-   If the user guesses a number that is smaller, we print “The number is too small”.
-   If the user is able to correctly guess the number, then we print “Correct
    Number!”.
-   At the end we will print the number that was generated by our Math library.
-   LET THE GUESSING BEGIN :)

```java
import java.lang.Math;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int random = (int) (Math.random()*100);
        int userInput = 0;

        do {
            System.out.print("Guess my number (1-100): ");
            userInput = sc.nextInt();
            if (userInput == random) {
                System.out.println("wow you are correct !");
            } else if (userInput > random) {
                System.out.println("Too large");
            } else {
                System.out.println("Too small");
            }
        } while (userInput >=0);

    }
}
```

```java
// output
Guess my number (1-100): 78
Too large
Guess my number (1-100): 49
Too large
Guess my number (1-100): 6
wow you are correct !
Guess my number (1-100):
```

<br>

**[⬆ Back to Top](#table-of-contents)**
<br>
