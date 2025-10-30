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

















