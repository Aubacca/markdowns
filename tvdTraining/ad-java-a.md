# Java for Developers - Basics (AD-JAVA-A)

## Java and the JDK

#### Java Platform, Standard Edition (Java SE)

Java SE's API provides the core functionality of the Java programming language. It defines everything from the basic types and objects of the Java programming language to high-level classes that are used for networking, security, database access, graphical user interface (GUI) development, and XML parsing.
In addition to the core API, the Java SE platform consists of a virtual machine, development tools, deployment technologies, and other class libraries and toolkits commonly used in Java technology applications.

#### Java Platform, Enterprise Edition (Java EE)

The Java EE platform is built on top of the Java SE platform. The Java EE platform provides an API and runtime environment for developing and running large-scale, multi-tiered, scalable, reliable, and secure network applications.

#### Java Platform, Micro Edition (Java ME)

The Java ME platform provides an API and a small-footprint virtual machine for running Java programming language applications on small devices, like mobile phones. The API is a subset of the Java SE API, along with special class libraries useful for small device application development. Java ME applications are often clients of Java EE platform services.

#### JavaFX

JavaFX is a platform for creating rich internet applications using a lightweight user-interface API. JavaFX applications use hardware-accelerated graphics and media engines to take advantage of higher-performance clients and a modern look-and-feel as well as high-level APIs for connecting to networked data sources. JavaFX applications may be clients of Java EE platform services.

#### JDK

The Java Development Kit (JDK) is a software development environment used for developing Java applications and applets. It includes the Java Runtime Environment (JRE), an interpreter/loader (java), a compiler (javac), an archiver (jar), a documentation generator (javadoc) and other tools needed in Java development.

### Internet

- <a href="https://docs.oracle.com/javaee/6/firstcup/doc/gcrlo.html" target="_blank">Understanding Java Platform, Enterprise Edition</a>
- <a href="https://www.oracle.com/technetwork/es/java/javase/tech/index.html" target="_blank">Oracle - Java SE Technologies</a>

### Samples

```java

```

## Introduction into Eclipse IDE

### Internet

- <a href="https://www.eclipse.org/" target="_blank">Eclipse</a>
- <a href="https://www.jetbrains.com/idea/" target="_blank">IntelliJ IDEA</a>

## Data Types and Variables

#### Primitive Datatypes

##### Internet

- <a href="https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html" target="_blank">Oracle Documentation - Primitive Data Types</a>

##### Samples

| Type    | Size in Bytes         | Range                                                                                             |
| ------- | --------------------- | ------------------------------------------------------------------------------------------------- |
| byte    | 1 byte                | -128 to 127                                                                                       |
| short   | 2 bytes               | -32,768 to 32,767                                                                                 |
| int     | 4 bytes               | -2,147,483,648 to 2,147,483, 647                                                                  |
| long    | 8 bytes               | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807                                           |
| float   | 4 bytes               | approximately ±3.40282347E+38F (6-7 significant decimal digits) Java implements IEEE 754 standard |
| char    | 2 byte                | 0 to 65,536 (unsigned)                                                                            |
| boolean | not precisely defined | true or false                                                                                     |

#### Enum Types

An enum type is a special data type that enables for a variable to be a set of predefined constants. The variable must be equal to one of the values that have been predefined for it. Common examples include compass directions (values of NORTH, SOUTH, EAST, and WEST) and the days of the week.

##### Internet

- <a href="https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html" target="_blank">Oracle Documentation - Enum Types</a>

##### Samples

```java
public enum Days {
   SUNDAY, MONDAY, TUESDAY, WEDNESDAY,
    THURSDAY, FRIDAY, SATURDAY
}
...

Days[] days = Days.values();
ArrayList<String> stringDay = new ArrayList<String>();
for (Days day : days) {
   stringDay.add(day.toString());
}
```

#### Literals

You may have noticed that the new keyword isn't used when initializing a variable of a primitive type. Primitive types are special data types built into the language; they are not objects created from a class. A literal is the source code representation of a fixed value; literals are represented directly in your code without requiring computation. As shown below, it's possible to assign a literal to a variable of a primitive type:

##### Samples

```java
// Literals
boolean result = true;
char capitalC = 'C';
byte b = 100;
short s = 10000;
int i = 100000;
```

#### Constant Variable

##### Samples

```java
static final int DAYS_IN_WEEK = 7;
```
#### Naming Conventions
##### Internet
- <a href="https://www.oracle.com/technetwork/java/codeconventions-135099.html" target="_blank">Oracle Documentation - Naming Conventions</a>

## Operators and Control Flow

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```


## Classes and Objects

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Inheritance Abstract classes Interfaces

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Arrays

### Internet

- <a href="https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html" target="_blank">Oracle Documentation - Arrays</a>

### Samples

```java
// preferred way.
double[] myList;
or
double myList[];

double[] myList = new double[10];
double[] myList = {1.9, 2.9, 3.4, 3.5};

// Print all the array elements
for (int i = 0; i < myList.length; i++) {
   System.out.println(myList[i] + " ");
}

// Print all the array elements
for (double element: myList) {
   System.out.println(element);
}
```

## String and Object

### Internet

- <a href="https://docs.oracle.com/javase/9/docs/api/java/lang/String.html" target="_blank">Oracle Documentation - Class String</a>

### Samples

```java
String greeting = "Hello world!";

String string1 = "saw I was ";
System.out.println("Dot " + string1 + "Tod");

String fs;
fs = String.format("The value of the float variable is " +
                   "%f, while the value of the integer " +
                   "variable is %d, and the string " +
                   "is %s", floatVar, intVar, stringVar);
System.out.println(fs);
```

## Utilities and Formatting

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Exception Handling

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Unit Testing

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```
