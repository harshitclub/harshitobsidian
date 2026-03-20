# 1. Functions in Dart

## 1.1 What is a Function?

A function is a **reusable block of code** that performs a specific task.
### Why Functions Matter

- Avoid code duplication
- Improve readability
- Enable modular design
- Easier testing and debugging

## 1.2 Function Declaration

### Basic Syntax

```
returnType functionName(parameters) {  
  // logic  
  return value;  
}
```
### Example

```
int add(int a, int b) {  
  return a + b;  
}
```

### Calling the Function

```
void main() {  
  int result = add(5, 3);  
  print(result);  
}
```

## 1.3 Function Types

### 1. Void Function (No Return)

```
void greet() {  
  print("Hello");  
}
```

### 2. Function with Return Value

```
int square(int num) {  
  return num * num;  
}
```

### 3. Dynamic Return Type (Not Recommended)

```
dynamic getValue() {  
  return "Hello";  
}
```
### Deep Insight
> Always prefer explicit types → improves maintainability and reduces bugs.
# 2. Parameters in Dart

## 2.1 Positional Parameters

### Syntax

```
void greet(String name, int age) {  
  print("Name: $name, Age: $age");  
}
```
### Call

```
greet("Harshit", 23);
```

### Characteristics
- Order matters
- Required by default

## 2.2 Optional Positional Parameters

### Syntax

```
void greet(String name, [int? age]) {  
  print("Name: $name, Age: $age");  
}
```

### Notes
- Wrapped in `[ ]`
- Can be null
- Must handle null safety

## 2.3 Named Parameters

### Syntax

```
void greet({required String name, int? age}) {  
  print("Name: $name, Age: $age");  
}
```

### Call

```
greet(name: "Harshit", age: 23);
```

### Key Features
- Order does not matter
- More readable
- Can be:
    - `required`    
    - optional

## 2.4 Default Values

```
void greet({String name = "Guest"}) {  
  print("Hello $name");  
}
```
### Insight
> Named parameters are preferred in large-scale applications for clarity.

# 3. Arrow Functions (Fat Arrow)

## 3.1 Definition

Short syntax for single-expression functions.

### Syntax

```
returnType functionName(parameters) => expression;
```

### Example

```
int add(int a, int b) => a + b;
```
### When to Use
- Single-line logic
- Cleaner code

### Avoid When
- Multiple statements needed
- Complex logic

# 4. Null Safety in Dart

This is one of Dart’s most important features.
## 4.1 What is Null Safety?
> Ensures variables cannot contain `null` unless explicitly allowed.
## 4.2 Nullable vs Non-Nullable

### Non-nullable (Default)

```
String name = "Harshit";
```

- Cannot be null
### Nullable

```
String? name;
```

- Can be null

## 4.3 The `?` Operator

Marks a variable as nullable.

```
int? age;
```

## 4.4 The `!` Operator (Null Assertion)

Forces Dart to treat a value as non-null.

```
String? name = "Harshit";  
print(name!);
```
### Risk
If value is null → runtime crash

## 4.5 The `late` Keyword

Used when variable is initialized later.

```
late String name;  
  
void main() {  
  name = "Harshit";  
  print(name);  
}
```
### Use Case

- When initialization is delayed but guaranteed
## 4.6 Null-Aware Operators

### 1. `??` (Default Value)

```
String name = input ?? "Guest";
```

### 2. `?.` (Safe Access)

```
name?.length;
```

### 3. `??=` (Assign if null)

```
name ??= "Default";
```

## 4.7 Deep Insight
> Null safety shifts errors from runtime → compile time  
> This is critical for building large-scale applications

# 5. Practical: Reusable Utility Functions

## Example

```
int add(int a, int b) => a + b;  
  
double calculateDiscount(double price, double discount) {  
  return price - (price * discount / 100);  
}  
  
bool isEven(int num) => num % 2 == 0;
```
## Usage

```
void main() {  
  print(add(5, 3));  
  print(calculateDiscount(100, 10));  
  print(isEven(4));  
}
```

# 6. Practical: Null Checks

## Example

```
void printName(String? name) {  
  if (name != null) {  
    print("Name: $name");  
  } else {  
    print("Name is null");  
  }  
}
```

## Alternative (Cleaner)

```
print("Name: ${name ?? "Guest"}");
```

# 7. Practical: Form-like CLI Input Validation

## Example Program

```
import 'dart:io';  
  
String getInput(String message) {  
  print(message);  
  return stdin.readLineSync() ?? "";  
}  
  
void main() {  
  String name = getInput("Enter your name:");  
  
  while (name.isEmpty) {  
    print("Name cannot be empty");  
    name = getInput("Enter your name again:");  
  }  
  
  print("Enter your age:");  
  int? age = int.tryParse(stdin.readLineSync() ?? "");  
  
  while (age == null || age <= 0) {  
    print("Invalid age. Enter again:");  
    age = int.tryParse(stdin.readLineSync() ?? "");  
  }  
  
  print("\n--- User Info ---");  
  print("Name: $name");  
  print("Age: $age");  
}
```

## Key Concepts Used

- Functions for reuse
- Null safety (`?`, `??`)
- Validation loops
- Safe parsing (`tryParse`)

# 8. Common Mistakes

## Mistake 1: Ignoring Null Safety

```
String name = null; // ❌ error
```

## Mistake 2: Overusing `!`

```
print(name!); // risky
```

## Mistake 3: Not Using `tryParse`

```
int age = int.parse(input); // may crash
```

Better:

```
int? age = int.tryParse(input);
```