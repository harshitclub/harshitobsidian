# 1. Dart Syntax Basics

## 1.1 Structure of a Dart Program

Every Dart program starts with a **main function**:

```
void main(){
 print("Hello World!")
}
```
### Key Points:

- `main()` is the **entry point**
- Execution always starts from here
- `void` → function returns nothing

## 1.2 Statements and Semicolons

- Each statement ends with `;`

```
int a = 10;  
print(a);
```

## 1.3 Comments

```
// Single-line comment  
  
/*  
Multi-line comment  
*/
```

## 1.4 Printing Output

```
print("Hello World");
```

- `print()` is used for console output
- Automatically adds a newline

## 1.5 Code Blocks

Defined using `{ }`

```
if (true) {  
print("Inside block");  
}
```

## 1.6 Naming Rules

- Variables use camelCase:
    - `userName`, `totalAmount`
- Cannot start with numbers
- Cannot use reserved keywords

# 2. Variables in Dart

## 2.1 What is a Variable?

A variable is a container that stores data in memory.

## 2.2 Types of Variable Declarations

## 2.2.1 `var` (Type Inference)

```
var name = "Harshit";  
var age = 23;
```

### Behavior:
- Dart automatically detects type
- Type becomes fixed after first assignment

```
var a = 10;  
a = 20; // ✅ allowed  
// a = "text"; ❌ error
```

## 2.2.2 Explicit Type

```
String name = "Harshit";  
int age = 23;
```
### Advantage:
- More readable
- Better for large codebases

## 2.2.3 `final` (Runtime Constant)

`final time = DateTime.now();`
### Key Points:
- Assigned only once
- Value determined at runtime

## 2.2.4 `const` (Compile-Time Constant)

```
const pi = 3.14;
```
### Key Points:
- Value must be known at compile time
- More optimized than `final`

## 2.3 Difference: `final` vs `const`

|Feature|final|const|
|---|---|---|
|Assignment|Once|Once|
|Time|Runtime|Compile-time|
|Use case|Dynamic values|Fixed values|


## 2.4 Deep Insight
> Use `const` whenever possible → improves performance  
> Use `final` when value is fixed but computed at runtime

# 3. Data Types in Dart

Dart is **strongly typed** and **type-safe**.

## 3.1 int

```
int age = 23;
```

- Whole numbers
- No decimals

## 3.2 double

```
double price = 99.99;
```

- Decimal numbers

## 3.3 String

```
String name = "Harshit";
```

- Text data
- Can use single or double quotes

## 3.4 bool

```
bool isLoggedIn = true;
```

- Only `true` or `false`

## 3.5 List (Array-like structure)

```
List<int> numbers = [1, 2, 3];
```

### Access elements:

```
print(numbers[0]); // 1
```

## 3.6 Dynamic

```
dynamic value = 10;  
value = "Hello";
```
### Insight:
- Avoid using `dynamic` unless necessary
- Breaks type safety

# 4. String Interpolation

## 4.1 Basic Interpolation

```
String name = "Harshit";  
print("Hello $name");
```

## 4.2 Expressions

```
int a = 5;  
int b = 3;  
print("Sum is ${a + b}");
```

## 4.3 Why It Matters

- Cleaner than concatenation
- More readable

# 5. Input/Output in Dart (CLI)

## 5.1 Output

```
print("Hello World");
```

## 5.2 Input from User (Console)

To take input, we use:

```
import 'dart:io';
```

## 5.3 Example: Basic Input

```
import 'dart:io';  
  
void main() {  
print("Enter your name:");  
String? name = stdin.readLineSync();  
  
print("Hello $name");  
}
```

### Key Concepts:

- `stdin.readLineSync()`:
    - Reads input from console
    - Returns `String?` (nullable)

## 5.4 Handling Null Safety

```
String name = stdin.readLineSync() ?? "Guest";
```

- If input is null → default value used

## 5.5 Converting Input Types

### String → int

```
int age = int.parse(stdin.readLineSync()!);
```
### String → double

```
double price = double.parse(stdin.readLineSync()!);
```

### Important Note:
- `!` means: “I am sure it's not null”
- Use carefully to avoid runtime errors

# 6. DartPad Examples with Variables

## Example 1: Variables Demo

```
void main() {  
var name = "Harshit";  
int age = 23;  
double height = 5.9;  
bool isDeveloper = true;  
  
print("Name: $name");  
print("Age: $age");  
print("Height: $height");  
print("Developer: $isDeveloper");  
}
```

## Example 2: List Example

```
void main() {  
List<String> fruits = ["Apple", "Banana", "Mango"];  
  
print("First fruit: ${fruits[0]}");  
}
```

# 7. Basic CLI App (Input + Output)

## Example: User Info App

```
import 'dart:io';  
  
void main() {  
print("Enter your name:");  
String name = stdin.readLineSync() ?? "Unknown";  
  
print("Enter your age:");  
int age = int.parse(stdin.readLineSync()!);  
  
print("Enter your city:");  
String city = stdin.readLineSync() ?? "Unknown";  
  
print("\n--- User Info ---");  
print("Name: $name");  
print("Age: $age");  
print("City: $city");  
}
```

## What This Teaches

- Input handling
- Type conversion
- String interpolation
- Basic CLI structure

# 8. Common Mistakes (Important)

## Mistake 1: Forgetting Null Safety

```
String name = stdin.readLineSync(); // ❌ error
```

Correct:

```
String? name = stdin.readLineSync();
```

## Mistake 2: Wrong Type Conversion

```
int age = stdin.readLineSync(); // ❌
```

Correct:

```
int age = int.parse(stdin.readLineSync()!);
```

## Mistake 3: Overusing `dynamic`

Avoid:
```
dynamic data = "Hello";
```

# 9. Deep Understanding (What Most People Miss)

## 9.1 Dart is Strongly Typed but Flexible

- Type inference (`var`)
- Strict type safety (no silent conversions)

## 9.2 Null Safety is Core

- Prevents runtime crashes
- Forces you to think about missing values

## 9.3 Variables Are Immutable by Default (Best Practice)

Prefer:
```
final name = "Harshit";
```


## Questions:
1. Write a program to print your name in Dart.
2. Write a program to print **Hello I am “John Doe”** and **Hello I’am “John Doe”** with single and double quotes.
3. Declare **constant type** of int set value 7.
4. Write a program in Dart that finds simple interest. `Formula= (p * t * r) / 100`
5. Write a program to print a square of a number using user input.