# 1. Control Flow in Dart

Control flow determines **how your program executes step-by-step**.

# 1.1 Conditional Statements

## 1.1.1 `if` Statement

### Syntax:

```
if (condition) {  
// code  
}
```
### Example:

```
int age = 18;  
  
if (age >= 18) {  
print("You are eligible to vote");  
}
```

## 1.1.2 `if-else`

```
int age = 16;  
  
if (age >= 18) {  
print("Adult");  
} else {  
print("Minor");  
}
```

## 1.1.3 `else if`

Used for multiple conditions:

```
int marks = 75;  
  
if (marks >= 90) {  
print("Grade A");  
} else if (marks >= 70) {  
print("Grade B");  
} else {  
print("Grade C");  
}
```
## 1.1.4 Deep Insight
> Conditions are evaluated top-down.  
> First true condition stops further checking.

## 1.1.5 `switch` Statement

Used when comparing one variable against multiple values.
### Syntax:

```
switch (value) {  
case 1:  
// code  
break;  
case 2:  
// code  
break;  
default:  
// fallback  
}
```

### Example:

```
int day = 3;  
  
switch (day) {  
case 1:  
print("Monday");  
break;  
case 2:  
print("Tuesday");  
break;  
case 3:  
print("Wednesday");  
break;  
default:  
print("Invalid day");  
}
```

### Important Notes:

- `break` is required to stop fall-through
- Works with:
    - int
    - String
    - enums

# 2. Loops in Dart

Loops are used to **repeat execution**.

## 2.1 `for` Loop

### Syntax:

```
for (initialization; condition; update) {  
// code  
}
```

### Example:

```
for (int i = 1; i <= 5; i++) {  
print(i);  
}
```

### Use Case:
- Known number of iterations

## 2.2 `while` Loop

### Syntax:

```
while (condition) {  
// code  
}
```

### Example:

```
int i = 1;  
  
while (i <= 5) {  
print(i);  
i++;  
}
```

### Use Case:
- Unknown number of iterations

## 2.3 `do-while` Loop

### Syntax:

```
do {  
// code  
} while (condition);
```

### Example:

```
int i = 1;  
  
do {  
print(i);  
i++;  
} while (i <= 5);
```

### Key Difference:
- Runs **at least once**, even if condition is false

# 3. Dart Compilation Process

## 3.1 High-Level Flow

Dart Code → Kernel IR → (JIT or AOT) → Native Code / JavaScript
## 3.2 Step-by-Step Breakdown

### Step 1: Dart Source Code

```
void main() {  
print("Hello");  
}
```

### Step 2: Kernel IR (Intermediate Representation)

- Dart converts code into **Kernel IR**
- Platform-independent format
- Used internally for optimization

### Step 3: Compilation Path

## Option 1: JIT (Just-In-Time)

- Used during development
- Compiled at runtime
### Flow:

Dart → Kernel → JIT → Machine Code

### Advantages:
- Fast development
- Hot reload support
### Disadvantages:
- Slower startup
- Not optimized for production

## Option 2: AOT (Ahead-Of-Time)
- Used in production

### Flow:

Dart → Kernel → AOT → Native Binary

### Advantages:
- Fast startup
- Better performance
- Optimized machine code

### Disadvantages:
- No hot reload
- Slower compilation

## 3.3 Dart → JavaScript (Web)

For web:

Dart → Kernel → JS Compiler → JavaScript

## 3.4 JIT vs AOT (Flutter Context)

|Feature|JIT (Dev)|AOT (Release)|
|---|---|---|
|Speed|Slower|Faster|
|Hot Reload|Yes|No|
|Compilation|Runtime|Before execution|
|Use Case|Development|Production|


## Deep Insight

> Flutter uses JIT for productivity and AOT for performance.  
> This dual-mode system is one of its biggest strengths.

# 4. Practical Programs

# 4.1 Program: Check Prime Number

## Logic:

- A number is prime if divisible only by 1 and itself

### Code:

```
import 'dart:io';  
  
void main() {  
print("Enter a number:");  
int num = int.parse(stdin.readLineSync()!);  
  
bool isPrime = true;  
  
if (num <= 1) {  
isPrime = false;  
} else {  
for (int i = 2; i <= num ~/ 2; i++) {  
if (num % i == 0) {  
isPrime = false;  
break;  
}  
}  
}  
  
if (isPrime) {  
print("$num is a Prime Number");  
} else {  
print("$num is NOT a Prime Number");  
}  
}
```

## Insight:
- Optimization: check till `num/2` (or √num for better performance)

# 4.2 Program: Reverse a String

## Logic:

- Traverse string backward
### Code:

```
import 'dart:io';  
  
void main() {  
print("Enter a string:");  
String input = stdin.readLineSync()!;  
  
String reversed = "";  
  
for (int i = input.length - 1; i >= 0; i--) {  
reversed += input[i];  
}  
  
print("Reversed string: $reversed");  
}
```

## Alternative (Built-in):

`String reversed = input.split('').reversed.join();`

# 4.3 Calculator with Menu (Switch + Loop)

## Features:
- Continuous execution
- Menu-driven system
- Uses switch + loop

### Code:
```
import 'dart:io';  
  
void main() {  
while (true) {  
print("\n--- Calculator ---");  
print("1. Add");  
print("2. Subtract");  
print("3. Multiply");  
print("4. Divide");  
print("5. Exit");  
  
int choice = int.parse(stdin.readLineSync()!);  
  
if (choice == 5) {  
print("Exiting...");  
break;  
}  
  
print("Enter first number:");  
double a = double.parse(stdin.readLineSync()!);  
  
print("Enter second number:");  
double b = double.parse(stdin.readLineSync()!);  
  
switch (choice) {  
case 1:  
print("Result: ${a + b}");  
break;  
case 2:  
print("Result: ${a - b}");  
break;  
case 3:  
print("Result: ${a * b}");  
break;  
case 4:  
if (b != 0) {  
print("Result: ${a / b}");  
} else {  
print("Cannot divide by zero");  
}  
break;  
default:  
print("Invalid choice");  
}  
}  
}
```
