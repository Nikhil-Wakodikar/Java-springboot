# SOLID Principles

SOLID is a set of five object-oriented design principles that help create maintainable, extensible, and understandable software.

| Letter | Principle |
|---|---|
| **S** | Single Responsibility Principle |
| **O** | Open/Closed Principle |
| **L** | Liskov Substitution Principle |
| **I** | Interface Segregation Principle |
| **D** | Dependency Inversion Principle |

---

## 1. Single Responsibility Principle (SRP)

### Definition

A class should have only one reason to change.

### Bad Example

The following `UserService` handles authentication, database operations, and email functionality:

```typescript
class UserService {
  login() {
    // Authentication logic
  }

  saveUser() {
    // Database logic
  }

  sendEmail() {
    // Email logic
  }
}
```

The class has three responsibilities. Changes to authentication, database operations, or email functionality could require modifying the same class.

### Better Example

```typescript
class AuthService {
  login() {
    // Authentication logic
  }
}

class UserRepository {
  saveUser() {
    // Database logic
  }
}

class EmailService {
  sendEmail() {
    // Email logic
  }
}
```

Now, each class has a focused responsibility.

**Remember:** One class should have one clear job, not necessarily only one method.

---

## 2. Open/Closed Principle (OCP)

### Definition

Software entities should be open for extension but closed for modification.

Suppose an application supports UPI and card payments. Later, it needs to add net banking support.

### Bad Example

```typescript
class PaymentService {
  pay(type: string) {
    if (type === "upi") {
      // UPI payment
    } else if (type === "card") {
      // Card payment
    }
  }
}
```

Adding a new payment method requires modifying the existing class and adding another condition.

### Better Example

```typescript
interface PaymentMethod {
  pay(amount: number): void;
}

class UpiPayment implements PaymentMethod {
  pay(amount: number): void {
    console.log("UPI payment:", amount);
  }
}

class CardPayment implements PaymentMethod {
  pay(amount: number): void {
    console.log("Card payment:", amount);
  }
}

class PaymentService {
  constructor(private payment: PaymentMethod) {}

  process(amount: number): void {
    this.payment.pay(amount);
  }
}
```

To support another payment method, create a new class that implements `PaymentMethod`. The existing `PaymentService` does not need to change.

**Remember:** Add new behavior through extension instead of repeatedly modifying stable business logic.

---

## 3. Liskov Substitution Principle (LSP)

### Definition

Objects of a child class should be usable in place of objects of the parent class without breaking expected behavior.

### Bad Example

```typescript
class Bird {
  fly(): void {
    console.log("Flying");
  }
}

class Sparrow extends Bird {}

class Penguin extends Bird {
  fly(): void {
    throw new Error("Penguins cannot fly");
  }
}
```

A function expecting any `Bird` may call `fly()`. Passing a `Penguin` causes an unexpected failure because the child class violates behavior promised by its parent.

### Better Example

```typescript
interface Bird {}

interface FlyingBird extends Bird {
  fly(): void;
}

class Sparrow implements FlyingBird {
  fly(): void {
    console.log("Flying");
  }
}

class Penguin implements Bird {}
```

Now only birds that can fly implement `FlyingBird`.

**Remember:** Inheritance must preserve the behavior promised by the parent type. Do not force subclasses to support behavior they cannot provide.

---

## 4. Interface Segergation Principle (ISP)

### Definition

Clients should not be forced to depend on methods they do not use.

### Bad Example

```typescript
interface Machine {
  print(): void;
  scan(): void;
  fax(): void;
}

class SimplePrinter implements Machine {
  print(): void {}

  scan(): void {
    throw new Error("Not supported");
  }

  fax(): void {
    throw new Error("Not supported");
  }
}
```

A simple printer must implement scanning and faxing even though it cannot perform those operations.

### Better Example

```typescript
interface Printer {
  print(): void;
}

interface Scanner {
  scan(): void;
}

interface Fax {
  fax(): void;
}

class SimplePrinter implements Printer {
  print(): void {
    console.log("Printing");
  }
}
```

Each class implements only the capabilities it actually supports.

**Remember:** Prefer small, focused interfaces over one large interface containing unrelated methods.

---

## 5. Dependency Inversion Principle (DIP)

### Definition

High-level modules should not depend directly on low-level modules. Both should depend on abstractions.

### Bad Example

```typescript
class MySQLDatabase {
  save(): void {
    console.log("Saved to MySQL");
  }
}

class UserService {
  private database = new MySQLDatabase();

  saveUser(): void {
    this.database.save();
  }
}
```

`UserService` directly creates a `MySQLDatabase` implementation. Switching to another database requires changing the service.

### Better Example

```typescript
interface Database {
  save(): void;
}

class MySQLDatabase implements Database {
  save(): void {
    console.log("Saved to MySQL");
  }
}

class UserService {
  constructor(private database: Database) {}

  saveUser(): void {
    this.database.save();
  }
}
```

Now `UserService` depends on the `Database` abstraction, so it can use a different implementation.

**Remember:** Depend on what a component needs, not on a specific implementation of that dependency.

---

## DIP vs. Dependency Injection

**Note:** DIP is not the same as Dependency Injection (DI).

- **DIP** is a design principle.
- **DI** is a technique for supplying dependencies.
- DI is one way to implement DIP.
