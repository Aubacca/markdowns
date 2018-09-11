# Java for Developers - Additionals

## Generics
### Internet
* <a href="https://docs.oracle.com/javase/tutorial/java/generics/index.html" target="_blank">Generics (Oracle Java Documentation)</a>
* <a href="https://en.wikipedia.org/wiki/Generics_in_Java" target="_blank">Wikipedia</a>
* <a href="https://www.youtube.com/results?search_query=java+generics" target="_blank">YouTube</a>

### Samples
```java
public class GenericMethodTest {
   // generic method printArray
   public static < E > void printArray( E[] inputArray ) {
      // Display array elements
      for(E element : inputArray) {
         System.out.printf("%s ", element);
      }
      System.out.println();
   }

   public static void main(String args[]) {
      // Create arrays of Integer, Double and Character
      Integer[] intArray = { 1, 2, 3, 4, 5 };
      Double[] doubleArray = { 1.1, 2.2, 3.3, 4.4 };
      Character[] charArray = { 'H', 'E', 'L', 'L', 'O' };

      System.out.println("Array integerArray contains:");
      printArray(intArray);   // pass an Integer array

      System.out.println("\nArray doubleArray contains:");
      printArray(doubleArray);   // pass a Double array

      System.out.println("\nArray characterArray contains:");
      printArray(charArray);   // pass a Character array
   }
}
```
```java
public class MaximumTest {
   // determines the largest of three Comparable objects
   
   public static <T extends Comparable<T>> T maximum(T x, T y, T z) {
      T max = x;   // assume x is initially the largest
      
      if(y.compareTo(max) > 0) {
         max = y;   // y is the largest so far
      }
      
      if(z.compareTo(max) > 0) {
         max = z;   // z is the largest now                 
      }
      return max;   // returns the largest object   
   }
   
   public static void main(String args[]) {
      System.out.printf("Max of %d, %d and %d is %d\n\n", 
         3, 4, 5, maximum( 3, 4, 5 ));

      System.out.printf("Max of %.1f,%.1f and %.1f is %.1f\n\n",
         6.6, 8.8, 7.7, maximum( 6.6, 8.8, 7.7 ));

      System.out.printf("Max of %s, %s and %s is %s\n","pear",
         "apple", "orange", maximum("pear", "apple", "orange"));
   }
}
```
```java
public class Box<T> {
   private T t;

   public void add(T t) {
      this.t = t;
   }

   public T get() {
      return t;
   }

   public static void main(String[] args) {
      Box<Integer> integerBox = new Box<Integer>();
      Box<String> stringBox = new Box<String>();
    
      integerBox.add(new Integer(10));
      stringBox.add(new String("Hello World"));

      System.out.printf("Integer Value :%d\n\n", integerBox.get());
      System.out.printf("String Value :%s\n", stringBox.get());
   }
}
```

## Collections
### Internet
* <a href="https://docs.oracle.com/javase/tutorial/collections/TOC.html" target="_blank">Collections (Oracle Java Documentation)</a>
* <a href="https://en.wikipedia.org/wiki/Collection_(abstract_data_type)" target="_blank">Wikipedia</a>
* <a href="https://www.youtube.com/results?search_query=java+collections" target="_blank">YouTube</a>

### java.util.ArrayList
```java
public class ArrayList<E>
  extends AbstractList<E>
  implements List<E>, RandomAccess, Cloneable, Serializable  
```

## Lambdas
### Internet
* <a href="https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html" target="_blank">Collections (Oracle Java Documentation)</a>
* <a href="https://en.wikipedia.org/wiki/Anonymous_function#Java" target="_blank">Wikipedia</a>
* <a href="https://www.youtube.com/results?search_query=java+Lambdas" target="_blank">YouTube</a>

### Samples

```java
public class LambdasTester {

   final static String salutation = "Hello! ";
   
   public static void main(String args[]) {
      GreetingService greetService1 = message -> 
      System.out.println(salutation + message);
      greetService1.sayMessage("Lambdas Sample.");
   }
	
   @java.lang.FunctionalInterface
   interface GreetingService {
      void sayMessage(String message);
   }
}
```

Output
```bash
Hello! Lambdas Sample.
```

### Syntax
```java
parameter -> expression body
```

### API Reference
* <a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html" target="_blank">see java.util.function</a>

## JDBC
### Internet
* <a href="https://docs.oracle.com/javase/tutorial/jdbc/index.html" target="_blank">Collections (Oracle Java Documentation)</a>
* <a href="https://en.wikipedia.org/wiki/Java_Database_Connectivity" target="_blank">Wikipedia</a>
* <a href="https://www.youtube.com/results?search_query=java+JDBC" target="_blank">YouTube</a>

### Frameworks
* <a href="http://commons.apache.org/proper/commons-dbutils/" target="_blank">Apache Commons: DbUtils</a>
* <a href="http://jdbi.org/" target="_blank">Jdbi</a>
* <a href="http://www.jooq.org/" target="_blank">JOOQ</a>
* <a href="https://docs.spring.io/spring/docs/3.0.x/spring-framework-reference/html/jdbc.html#jdbc-core" target="_blank">Spring: JdbcTemplate</a>
* <a href="https://www.sql2o.org/" target="_blank">sql2o</a>


## Threads
##
# Internet
* <a href="https://docs.oracle.com/javase/9/docs/api/java/lang/Thread.html" target="_blank">Collections (Oracle Java Documentation)</a>
* <a href="https://en.wikipedia.org/wiki/Java_concurrency" target="_blank">Wikipedia</a>
* <a href="https://www.youtube.com/results?search_query=java+Threads" target="_blank">YouTube</a>

### Examples
```java
public class ThreadDemo extends Thread {
   private Thread t;
   private String threadName;
   
   ThreadDemo( String name) {
      threadName = name;
      System.out.println("Creating " +  threadName );
   }
   
   public void run() {
      System.out.println("Running " +  threadName );
      try {
         for(int i = 4; i > 0; i--) {
            System.out.println("Thread: " + threadName + ", " + i);
            Thread.sleep(250); // Let the thread sleep for a while.
         }
      } catch (InterruptedException e) {
         System.out.println("Thread " +  threadName + " interrupted.");
      }
      System.out.println("Thread " +  threadName + " exiting.");
   }
   
   public void start () {
      System.out.println("Starting " +  threadName );
      if (t == null) {
         t = new Thread (this, threadName);
         t.start ();
      }
   }
}

public class TestThread {
   public static void main(String args[]) {
      ThreadDemo T1 = new ThreadDemo( "Thread-1");
      T1.start();
      
      ThreadDemo T2 = new ThreadDemo( "Thread-2");
      T2.start();
   }   
}
```

## Annotations
### Internet
* <a href="https://docs.oracle.com/javase/tutorial/java/annotations/" target="_blank">Collections (Oracle Java Documentation)</a>
* <a href="https://en.wikipedia.org/wiki/Java_annotation" target="_blank">Wikipedia</a>
* <a href="https://www.youtube.com/results?search_query=java+Annotations" target="_blank">YouTube</a>
### Examples
```java
class ...
```

## JavaBeans
_JavaBeans are classes that encapsulate many objects into a single object (the bean). They are serializable, have a zero-argument constructor, and allow access to properties using getter and setter methods. The name "Bean" was given to encompass this standard, which aims to create reusable software components for Java._
### Internet
* <a href="https://docs.oracle.com/javase/8/docs/technotes/guides/beans/index.html" target="_blank">Collections (Oracle Java Documentation)</a>
* <a href="https://en.wikipedia.org/wiki/JavaBeans" target="_blank">Wikipedia</a>
* <a href="https://www.youtube.com/results?search_query=java+JavaBeans" target="_blank">YouTube</a>

### Examples
```java
public class PersonBean implements java.io.Serializable {
   private String firstName = null;
   private String lastName = null;
   private int age = 0;

   public PersonBean() {}
   public String getFirstName(){return firstName;}
   public String getLastName(){return lastName;}
   public int getAge(){return age;}
   public void setFirstName(String firstName){this.firstName = firstName;}
   public void setLastName(String lastName){this.lastName = lastName;}
   public void setAge(Integer age){this.age = age;}
}
```

### JavaBeans vs. POJOs (Plain-Old-Java-Object)
* **A JavaBean follows certain conventions**. See JavaBeans Conventions for more details.
    * Getter/setter naming
    * having a public default constructor
    * being serialisable
    * etc.   
* A **POJO isn't rigorously defined**. It's a Java object that doesn't have a requirement to implement a particular interface or derive from a particular base class, or make use of particular annotations in order to be compatible with a given framework, and can be any arbitrary (often relatively simple) Java object.

