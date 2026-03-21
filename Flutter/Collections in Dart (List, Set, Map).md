# 1. Introduction to Collections

## What are Collections?

Collections are data structures used to **store and manage multiple values** efficiently.
### Types in Dart:

- List → ordered collection
- Set → unique unordered collection
- Map → key-value pairs

## Why Collections Matter

- Handle real-world data (users, products, logs)
- Enable efficient data processing
- Foundation for backend + frontend logic

# 2. List in Dart

## 2.1 What is a List?

A **List** is an ordered collection of elements (like an array).

## 2.2 Declaration

```
List<int> numbers = [1, 2, 3, 4];
```

OR

```
var numbers = [1, 2, 3];
```

## 2.3 Accessing Elements

```
print(numbers[0]); // 1
```

## 2.4 Common List Methods

### 1. Add Element

```
numbers.add(5);
```
### 2. Add Multiple

```
numbers.addAll([6, 7]);
```
### 3. Remove Element

```
numbers.remove(3);
```
### 4. Remove at Index

```
numbers.removeAt(0);
```
### 5. Length

```
print(numbers.length);
```
### 6. Contains

```
print(numbers.contains(2));
```
### 7. Iterate

```
for (var num in numbers) {  
  print(num);  
}
```

## 2.5 List Types

### Fixed Length

```
var list = List.filled(3, 0);
```
### Growable List

```
var list = [1, 2, 3];  
list.add(4);
```
## 2.6 Deep Insight

> Lists are optimized for **ordered data and indexing**, not uniqueness.
# 3. Set in Dart

## 3.1 What is a Set?

A **Set** is a collection of **unique elements**.
## 3.2 Declaration

```
Set<int> numbers = {1, 2, 3};
```
## 3.3 Key Properties

- No duplicate values
- Unordered
- Fast lookup
## 3.4 Example

```
var nums = {1, 2, 2, 3};  
print(nums); // {1, 2, 3}
```
## 3.5 Common Methods

### Add

```
nums.add(4);
```
### Remove

```
nums.remove(2);
```
### Contains

```
nums.contains(3);
```

## 3.6 Deep Insight

> Sets are implemented using **hashing**, making them efficient for:

- Checking existence
- Removing duplicates

# 4. List vs Set

|Feature|List|Set|
|---|---|---|
|Order|Maintained|Not guaranteed|
|Duplicates|Allowed|Not allowed|
|Access|Index-based|No index|
|Use Case|Ordered data|Unique data|

## Real Use Case

- List → product list, chat messages
- Set → unique tags, unique user IDs
# 5. Map in Dart

## 5.1 What is a Map?

A **Map** stores data in **key-value pairs**.

## 5.2 Declaration

```
Map<String, String> phoneBook = {  
  "John": "12345",  
  "Alice": "67890"  
};
```

## 5.3 Access Value

```
print(phoneBook["John"]);
```
## 5.4 Add / Update

```
phoneBook["Bob"] = "11111";
```

## 5.5 Remove

```
phoneBook.remove("John");
```

## 5.6 Check Key

```
phoneBook.containsKey("Alice");
```

## 5.7 Loop Through Map

### Keys

```
for (var key in phoneBook.keys) {  
  print(key);  
}
```
### Values

```
for (var value in phoneBook.values) {  
  print(value);  
}

```
### Key-Value

```
phoneBook.forEach((key, value) {  
  print("$key: $value");  
});
```

## 5.8 Deep Insight

> Maps are implemented using hash tables → very fast lookup (O(1))

# 6. Looping Through Collections

## 6.1 For Loop

```
for (int i = 0; i < numbers.length; i++) {  
  print(numbers[i]);  
}
```

## 6.2 For-in Loop

```
for (var item in numbers) {  
  print(item);  
}
```
## 6.3 forEach

```
numbers.forEach((item) {  
  print(item);  
});
```
## Best Practice

- Use `for-in` for readability
- Use `forEach` for functional style

# 7. Practical: Phonebook App (Using Map)

## Features:

- Add contact
- View contacts
- Search contact

### Code

```
import 'dart:io';  
  
void main() {  
  Map<String, String> phoneBook = {};  
  
  while (true) {  
    print("\n--- Phonebook ---");  
    print("1. Add Contact");  
    print("2. View Contacts");  
    print("3. Search Contact");  
    print("4. Exit");  
  
    int choice = int.parse(stdin.readLineSync()!);  
  
    switch (choice) {  
      case 1:  
        print("Enter name:");  
        String name = stdin.readLineSync()!;  
        print("Enter number:");  
        String number = stdin.readLineSync()!;  
        phoneBook[name] = number;  
        print("Contact added");  
        break;  
  
      case 2:  
        phoneBook.forEach((key, value) {  
          print("$key: $value");  
        });  
        break;  
  
      case 3:  
        print("Enter name to search:");  
        String name = stdin.readLineSync()!;  
        print(phoneBook[name] ?? "Not found");  
        break;  
  
      case 4:  
        return;  
  
      default:  
        print("Invalid choice");  
    }  
  }  
}
```

# 8. Practical: Student Grade Tracker (List + Map)

## Concept:

- List of students
- Each student → Map

### Code

```
void main() {  
  List<Map<String, dynamic>> students = [  
    {"name": "Harshit", "marks": 85},  
    {"name": "Aman", "marks": 72},  
    {"name": "Riya", "marks": 90}  
  ];  
  
  for (var student in students) {  
    String name = student["name"];  
    int marks = student["marks"];  
  
    String grade;  
  
    if (marks >= 90) {  
      grade = "A";  
    } else if (marks >= 75) {  
      grade = "B";  
    } else {  
      grade = "C";  
    }  
  
    print("$name → Marks: $marks → Grade: $grade");  
  }  
}
```

## Insight

- List = collection of records
- Map = structure of each record

👉 This is how real backend data is structured.

# 9. Common Mistakes

## Mistake 1: Using List Instead of Set for Uniqueness

```
var list = [1, 2, 2]; // duplicates allowed
```
## Mistake 2: Accessing Missing Map Key

```
print(map["key"]); // may return null
```
## Mistake 3: Ignoring Types

```
List data = [1, "text"]; // avoid
```