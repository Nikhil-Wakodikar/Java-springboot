# Common Design Patterns in C#

## 1. Singleton Pattern

### Meaning

A class should have only one shared instance, and every caller should access that same instance.

**Real-world example:** Application configuration, where multiple services need access to the same settings.

### C# Example

```csharp
public class AppConfig
{
    private static AppConfig instance;

    private AppConfig()
    {
    }

    public static AppConfig GetInstance()
    {
        if (instance == null)
        {
            instance = new AppConfig();
        }

        return instance;
    }

    public string GetAppName()
    {
        return "Library Management";
    }
}
```

### Usage

```csharp
AppConfig config1 = AppConfig.GetInstance();
AppConfig config2 = AppConfig.GetInstance();

Console.WriteLine(
    Object.ReferenceEquals(config1, config2)
);
```

### Output

```text
True
```

### How It Works

1. The `private` constructor prevents other classes from creating instances directly.
2. `GetInstance()` creates the instance if it does not exist.
3. Every subsequent call returns the same instance.

**When to use:** When one shared instance is genuinely required.

**Interview definition:** Singleton restricts a class to one instance and provides a global access point to it.

---

## 2. Factory Method Pattern

### Meaning

Separate object creation from the code that uses the object.

**Real-world example:** An application needs to send email or SMS notifications. Without a factory, the calling code may need to know which concrete class to instantiate.

### C# Example

First, create an interface:

```csharp
public interface INotification
{
    string Send();
}
```

Create two implementations:

```csharp
public class EmailNotification : INotification
{
    public string Send()
    {
        return "Email sent";
    }
}

public class SmsNotification : INotification
{
    public string Send()
    {
        return "SMS sent";
    }
}
```

Create a simple factory:

```csharp
public class NotificationFactory
{
    public INotification CreateNotification(string type)
    {
        if (type == "Email")
        {
            return new EmailNotification();
        }

        if (type == "SMS")
        {
            return new SmsNotification();
        }

        throw new ArgumentException("Invalid notification type");
    }
}
```

### Usage

```csharp
NotificationFactory factory = new NotificationFactory();

INotification notification =
    factory.CreateNotification("Email");

string result = notification.Send();

Console.WriteLine(result);
```

### Output

```text
Email sent
```

### How It Works

1. The factory decides which object to create.
2. The calling code requests an object without constructing it directly.
3. The returned object is used through the `INotification` interface.

**When to use:** When object creation depends on a type, condition, or configuration.

**Interview definition:** Factory Method delegates object creation to a specialized creation method.

> **Note:** The example above is a Simple Factory. The formal Factory Method pattern uses an overridable creation method so subclasses can choose the concrete product.

---

## 3. Facade Pattern

### Meaning

Provide one simple interface to a complex system.

**Real-world example:** Placing an online order might require inventory validation, payment processing, and shipping arrangement. The customer should not need to call each subsystem separately.

### C# Example

Create three subsystem classes:

```csharp
public class InventoryService
{
    public string CheckStock()
    {
        return "Stock checked";
    }
}

public class PaymentService
{
    public string ProcessPayment()
    {
        return "Payment completed";
    }
}

public class ShippingService
{
    public string ShipOrder()
    {
        return "Order shipped";
    }
}
```

Now create the facade:

```csharp
public class OrderFacade
{
    private InventoryService inventory;
    private PaymentService payment;
    private ShippingService shipping;

    public OrderFacade()
    {
        inventory = new InventoryService();
        payment = new PaymentService();
        shipping = new ShippingService();
    }

    public string PlaceOrder()
    {
        string result = inventory.CheckStock();

        result += "\n" + payment.ProcessPayment();

        result += "\n" + shipping.ShipOrder();

        return result;
    }
}
```

### Usage

```csharp
OrderFacade order = new OrderFacade();

string result = order.PlaceOrder();

Console.WriteLine(result);
```

### Output

```text
Stock checked
Payment completed
Order shipped
```

### How It Works

1. `InventoryService`, `PaymentService`, and `ShippingService` handle separate tasks.
2. `OrderFacade` coordinates those services.
3. The caller only needs to call `PlaceOrder()`.

**When to use:** When a system has multiple operations or subsystems and you want to simplify how callers interact with them.

**Interview definition:** Facade provides a simplified interface to a complex set of classes or subsystems.

> **Note:** In a real payment workflow, you must also handle failures. For example, do not ship an order if payment fails.
