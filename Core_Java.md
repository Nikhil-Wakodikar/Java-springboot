# Core Java Interview Topics

## 1. Java Fundamentals

**Priority: High**

- What is Java? What are its features?
- JDK vs. JRE vs. JVM
- How Java code executes internally
- Platform independence
- Primitive vs. non-primitive data types
- Type casting
- Variables and data types
- Operators
- Conditional statements
- Loops
- Arrays
- Wrapper classes
- Autoboxing and unboxing

## 2. Object-Oriented Programming (OOP)

**Priority: Very High**

This is one of the most important interview sections.

- Class and object
- Constructors and constructor overloading
- Inheritance and its types
- Polymorphism
  - Compile-time polymorphism
  - Runtime polymorphism
- Method overloading vs. method overriding
- Encapsulation
- Abstraction
- Abstract class vs. interface
- `this` keyword
- `super` keyword
- `static` keyword
- `final` keyword

## 3. String Handling

**Priority: Very High**

- Strings in Java
- String pool
- `String` vs. `StringBuilder` vs. `StringBuffer`
- Why is `String` immutable?
- `==` vs. `equals()`
- `equals()` vs. `hashCode()`
- String concatenation
- Common `String` methods

## 4. Exception Handling

- What is an exception?
- Checked vs. unchecked exceptions
- `Error` vs. `Exception`
- `try`, `catch`, and `finally`
- `throw` vs. `throws`
- Custom exceptions
- Multiple `catch` blocks
- Exception propagation
- Try-with-resources

## 5. Collections Framework

**Priority: Very High**

One of the most frequently asked topics.

- What is the Collections Framework?
- `List` vs. `Set` vs. `Map`
- `ArrayList` vs. `LinkedList`
- `HashSet` vs. `TreeSet` vs. `LinkedHashSet`
- `HashMap` vs. `Hashtable`
- How `HashMap` works internally
- `HashMap` vs. `ConcurrentHashMap`
- `Iterator` vs. `ListIterator`
- `Comparable` vs. `Comparator`
- Fail-fast vs. fail-safe iterators
- `Queue` and `PriorityQueue`

## 6. Java 8+ Features

**Priority: Very High**

- Lambda expressions
- Functional interfaces
- `Predicate`, `Consumer`, `Supplier`, and `Function`
- Stream API
- `filter()`, `map()`, and `flatMap()`
- `reduce()`
- `collect()`
- `forEach()`
- `Optional` class
- Method references
- Default and static methods in interfaces
- Date and Time API

## 7. Multithreading and Concurrency

- Process vs. thread
- Thread lifecycle
- Creating threads
- `Thread` class vs. `Runnable` interface
- `Callable` vs. `Runnable`
- Synchronization
- `synchronized` keyword
- Deadlock
- Race condition
- `wait()`, `notify()`, and `notifyAll()`
- `ExecutorService`
- `Future` and `CompletableFuture`
- `volatile` keyword

## 8. JVM and Memory Management

- JVM architecture
- Heap vs. stack memory
- Method area
- Garbage collection
- Types of garbage collectors
- Object lifecycle
- Memory leaks
- ClassLoader
- JIT compiler
- Strong, weak, and soft references

## 9. Advanced Core Java

- Generics
- Enums
- Annotations
- Reflection API
- Serialization and deserialization
- Cloning
- Shallow copy vs. deep copy
- Immutable classes
- Java records
- Sealed classes


# Java



## What is Java?

Java is a high-level, object-oriented, and platform-independent programming language used to develop web, mobile, and desktop applications, as well as enterprise software.

### Example

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

## Key Features

- **Platform-independent:** Java code can run on different operating systems using the Java Virtual Machine (JVM).
- **Object-oriented:** Java uses classes and objects to organize code.
- **Simple:** Java has easy-to-understand syntax and avoids complex features like pointers.
- **Robust:** Java handles errors and manages memory automatically through garbage collection.
- **Multithreaded:** Java allows multiple tasks to run simultaneously.

## 🧩 1. Data Types, Variables, Loops, and Conditionals
**🔸 Primitive Data Types (8 types)**
| Type      | Size    | Example                       | Description                  |
| --------- | ------- | ----------------------------- | ---------------------------- |
| `byte`    | 1 byte  | `byte age = 22;`              | small integer                |
| `short`   | 2 bytes | `short salary = 20000;`       | small integer                |
| `int`     | 4 bytes | `int count = 100;`            | common integer type          |
| `long`    | 8 bytes | `long population = 9000000L;` | large integer (note the `L`) |
| `float`   | 4 bytes | `float price = 45.5f;`        | decimal with `f`             |
| `double`  | 8 bytes | `double gpa = 8.9;`           | more precise decimal         |
| `char`    | 2 bytes | `char grade = 'A';`           | single character             |
| `boolean` | 1 bit   | `boolean isActive = true;`    | true/false                   |

**🔸 Non-Primitive Data Types**
- String, Array, Class, Interface, etc.
Example:
```
String city = "Pune";
int[] marks = {90, 85, 88};
```
**🔹 3. Conditional Statements**
`✅ if / else`
```
int age = 18;

if (age >= 18) {
    System.out.println("Eligible to vote");
} else {
    System.out.println("Not eligible");
}
```

`✅ else if ladder`
```
int marks = 75;

if (marks >= 90) {
    System.out.println("A grade");
} else if (marks >= 75) {
    System.out.println("B grade");
} else {
    System.out.println("C grade");
}
```
`✅ switch statement`
```
int day = 3;

switch (day) {
    case 1: System.out.println("Monday"); break;
    case 2: System.out.println("Tuesday"); break;
    case 3: System.out.println("Wednesday"); break;
    default: System.out.println("Invalid day");
}
```

















