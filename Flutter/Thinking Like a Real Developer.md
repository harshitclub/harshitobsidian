# 1. The Real Problem (Why OOP Exists)

Before OOP, we wrote code like this:

```
String userName = "Aman";  
int userAge = 22;  
  
void login() {  
  print("$userName logged in");  
}
```
### Problem with this approach

- Data is scattered
- No structure
- Hard to scale
- Difficult to manage multiple users
### Think About This

If you have:

- 1 user → manageable
- 100 users → confusing
- 10,000 users → impossible
### Conclusion

We need a way to:
- Group related data
- Attach behavior to that data
- Manage multiple entities

That is where OOP comes in.

# 2. Class and Object (Core Foundation)

## Real-Life Analogy

Think of a **Car**:

**Every car has:**
- color
- speed
- brand

**And actions:**
- start()
- stop()
## Step 1: Create a Class (Blueprint)

```
class Car {  
  String color;  
  int speed;  
  
  void start() {  
    print("Car started");  
  }  
}
```
## Explanation

- `class Car` → blueprint
- `color`, `speed` → properties (data)
- `start()` → behavior (function inside class)

## Step 2: Create Object (Real Instance)

```
void main() {  
  Car car1 = Car();  
  
  car1.color = "Red";  
  car1.speed = 100;  
  
  print(car1.color);  
  car1.start();  
}
```
## Explanation

- `car1` is a real object
- It has its own data
- It can perform actions
## Key Understanding

- Class = design
- Object = real-world instance
# 3. Why Constructor is Needed

Problem:

```
Car car1 = Car();  
car1.color = "Red";  
car1.speed = 100;
```

Too many steps. Not clean.
## Solution: Constructor

```
class Car {  
  String color;  
  int speed;  
  
  Car(this.color, this.speed);  
}
```
## Usage

```
Car car1 = Car("Red", 100);
```
## Explanation

- Constructor initializes object at creation
- Cleaner and more efficient
# 4. Encapsulation (Protecting Data)

## Real Problem

**Imagine a bank account:**

```
class BankAccount {  
  double balance = 0;  
}
```

**Anyone can do:**

```
account.balance = -100000;
```
## Problem

- No control over data
- Unsafe
## Solution: Encapsulation

```
class BankAccount {  
  double _balance = 0;  
  
  void deposit(double amount) {  
    _balance += amount;  
  }  
  
  double getBalance() {  
    return _balance;  
  }  
}
```
## Explanation

- `_balance` → private
- Access only through methods
- You control how data changes
## Key Idea

Encapsulation =  Control + Safety + Structure
# 5. Inheritance (Reusing Code)

## Real Problem

You create:

```
class User {  
  String name;  
  int age;  
  
  void login() {  
    print("User logged in");  
  }  
}
```

Now you need:
- Admin
- Customer
## Without Inheritance

You repeat code again → bad practice
## With Inheritance

```
class User {  
  String name;  
  int age;  
  
  User(this.name, this.age);  
  
  void login() {  
    print("$name logged in");  
  }  
}  
  
class Admin extends User {  
  Admin(String name, int age) : super(name, age);  
  
  void deleteUser() {  
    print("User deleted");  
  }  
}
```

## Usage

```
Admin admin = Admin("Aman", 25);  
admin.login();  
admin.deleteUser();
```
## Explanation

- Admin reuses User properties
- Adds its own functionality
## Key Idea

Inheritance = reuse + extension

# 6. Polymorphism (Same Method, Different Behavior)

## Problem

Different users behave differently.

## Example

```
class User {  
  void accessPanel() {  
    print("User Panel");  
  }  
}  
  
class Admin extends User {  
  @override  
  void accessPanel() {  
    print("Admin Panel");  
  }  
}
```
## Usage

```
User user = Admin();  
user.accessPanel();
```
## Explanation

- Same method → different output
- Behavior depends on object type
## Key Idea

Polymorphism = flexibility

# 7. Abstraction (Hiding Complexity)

## Real Example

You drive a car:
- You press start button
- You don’t know engine internals
## In Code

```
abstract class Payment {  
  void pay();  
}  
  
class UPI extends Payment {  
  @override  
  void pay() {  
    print("Payment via UPI");  
  }  
}
```
## Explanation

- Abstract class defines rule
- Child class implements logic
## Key Idea

Abstraction = hide complexity, show essentials
# 8. Full Real-World Example (User System)

Now combine everything.

```
abstract class User {  
  String name;  
  
  User(this.name);  
  
  void login();  
  
  void display() {  
    print("User: $name");  
  }  
}  
  
class Admin extends User {  
  Admin(String name) : super(name);  
  
  @override  
  void login() {  
    print("Admin logged in");  
  }  
  
  void deleteUser() {  
    print("User deleted");  
  }  
}  
  
class Customer extends User {  
  Customer(String name) : super(name);  
  
  @override  
  void login() {  
    print("Customer logged in");  
  }  
}
```
## Usage

```
void main() {  
  Admin admin = Admin("Aman");  
  Customer customer = Customer("Ravi");  
  
  admin.login();  
  admin.deleteUser();  
  
  customer.login();  
}
```


---

## Real Implementation Examples

# 1. Class & Object (Basic Understanding)

## Program: Car System

```
void main() {  
  Car car1 = Car("Red", 120);  
  Car car2 = Car("Blue", 90);  
  
  car1.display();  
  car2.display();  
}  
  
class Car {  
  String color;  
  int speed;  
  
  // Constructor  
  Car(this.color, this.speed);  
  
  void display() {  
    print("Car Color: $color, Speed: $speed");  
  }  
}
```
## Output

```
Car Color: Red, Speed: 120  
Car Color: Blue, Speed: 90
```
## Notes

- Each object has its own data
- Same class → multiple objects
# 2. Encapsulation (Data Protection)

## Program: Bank Account

```
void main() {  
  BankAccount account = BankAccount();  
  
  account.deposit(5000);  
  account.withdraw(2000);  
  
  print("Current Balance: ${account.getBalance()}");  
}  
  
class BankAccount {  
  double _balance = 0;  
  
  void deposit(double amount) {  
    _balance += amount;  
    print("Deposited: $amount");  
  }  
  
  void withdraw(double amount) {  
    if (amount <= _balance) {  
      _balance -= amount;  
      print("Withdrawn: $amount");  
    } else {  
      print("Insufficient Balance");  
    }  
  }  
  
  double getBalance() {  
    return _balance;  
  }  
}
```
## Output

```
Deposited: 5000  
Withdrawn: 2000  
Current Balance: 3000
```
## Notes

- Direct access not allowed
- Control via methods

# 3. Inheritance (Reuse Code)

## Program: User → Admin

```
void main() {  
  Admin admin = Admin("Aman", 25);  
  
  admin.login();  
  admin.deleteUser();  
}  
  
class User {  
  String name;  
  int age;  
  
  User(this.name, this.age);  
  
  void login() {  
    print("$name logged in");  
  }  
}  
  
class Admin extends User {  
  Admin(String name, int age) : super(name, age);  
  
  void deleteUser() {  
    print("Admin deleted a user");  
  }  
}
```
## Output

```
Aman logged in  
Admin deleted a user
```
## Notes

- Admin reused login()
- No need to rewrite code
# 4. Polymorphism (Different Behavior)

## Program: Different Users

```
void main() {  
  User user1 = Admin();  
  User user2 = Customer();  
  
  user1.accessPanel();  
  user2.accessPanel();  
}  
  
class User {  
  void accessPanel() {  
    print("User Panel");  
  }  
}  
  
class Admin extends User {  
  @override  
  void accessPanel() {  
    print("Admin Panel");  
  }  
}  
  
class Customer extends User {  
  @override  
  void accessPanel() {  
    print("Customer Panel");  
  }  
}
```
## Output

```
Admin Panel  
Customer Panel
```
## Notes

- Same method → different outputs
- Based on object types
# 5. Abstraction (Rules + Implementation)

## Program: Payment System

```
void main() {  
  Payment p1 = UPI();  
  Payment p2 = Card();  
  
  p1.pay();  
  p2.pay();  
}  
  
abstract class Payment {  
  void pay();  
}  
  
class UPI extends Payment {  
  @override  
  void pay() {  
    print("Payment done using UPI");  
  }  
}  
  
class Card extends Payment {  
  @override  
  void pay() {  
    print("Payment done using Card");  
  }  
}
```
## Output

```
Payment done using UPI  
Payment done using Card
```
## Notes

- Payment defines rule
- Each class implements differently

# 6. Full Real-World Program (Combine Everything)

## Program: Mini User System

```
void main() {  
  Admin admin = Admin("Aman");  
  Customer customer = Customer("Ravi");  
  
  admin.login();  
  admin.deleteUser();  
  
  customer.login();  
}  
  
abstract class User {  
  String name;  
  
  User(this.name);  
  
  void login();  
}  
  
class Admin extends User {  
  Admin(String name) : super(name);  
  
  @override  
  void login() {  
    print("Admin $name logged in");  
  }  
  
  void deleteUser() {  
    print("Admin deleted a user");  
  }  
}  
  
class Customer extends User {  
  Customer(String name) : super(name);  
  
  @override  
  void login() {  
    print("Customer $name logged in");  
  }  
}
```
## Output

```
Admin Aman logged in  
Admin deleted a user  
Customer Ravi logged in
```