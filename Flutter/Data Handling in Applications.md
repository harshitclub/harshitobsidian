## 1. Problem Statement

In real applications, we rarely deal with a single value.

We often need to:
- Store multiple users
- Manage structured data
- Process large datasets efficiently
### Example Problems
- Store list of students
- Avoid duplicate entries
- Store user details (name, age, email)
- Perform operations on multiple values

## 2. List (Ordered Collection)

### Definition

A List is an ordered collection of elements.
### Syntax

```
List<String> users = ["Aman", "Ravi", "Neha"];
```
### Characteristics
- Maintains order
- Allows duplicate values
- Access using index
### Example

```
print(users[0]); // Aman
```
### Common Operations

```
users.add("Rahul");  
users.remove("Aman");  
print(users.length);
```

### Observation

```
List<String> users = ["Aman", "Ravi", "Aman"];
```

- Duplicate values are allowed

## 3. Set (Unique Collection)

### Definition

A Set is an unordered collection of unique elements.
### Syntax

```
Set<String> users = {"Aman", "Ravi", "Aman"};  
print(users);
```
### Characteristics
- No duplicate values
- Unordered
- Faster lookup compared to List
### Use Case
- When uniqueness is required
- Example: usernames, IDs

### Example Conversion

```
List<int> numbers = [1,2,2,3,4,4];  
Set<int> uniqueNumbers = numbers.toSet();  
print(uniqueNumbers);
```

## 4. Map (Key-Value Structure)

### Definition
A Map stores data in key-value pairs.
### Syntax
```
Map<String, dynamic> user = {  
  "name": "Aman",  
  "age": 22  
};
```
### Characteristics
- Each key is unique
- Values can be of any type
- Access via keys
### Accessing Data

```
print(user["name"]);
```
### Updating Data

```
user["email"] = "aman@gmail.com";
```

### Use Case
- Structured data
- Example: user profile, product details

## 5. Loops (Iteration)

### Purpose

Used to process multiple elements efficiently.
### For Loop

```
for (int i = 0; i < 5; i++) {  
  print(i);  
}
```
### For-in Loop

```
List<String> users = ["Aman", "Ravi", "Neha"];  
  
for (var user in users) {  
  print(user);  
}
```
### Iterating Map

```
Map<String, int> marks = {  
  "Aman": 90,  
  "Ravi": 85  
};  
  
for (var key in marks.keys) {  
  print("$key: ${marks[key]}");  
}
```

## 6. Functions (Reusable Logic)

### Definition

Functions are used to organize and reuse code.
### Basic Function

```
void greet() {  
  print("Hello");  
}
```

# Make a calculator using functions:
  # Take input from users num1 and num2
  # Make features like - add, subtract, divide and multiply
### Function with Parameters

```
void greetUser(String name) {  
  print("Hello $name");  
}
```
### Function with Return Value

```
int square(int num) {  
  return num * num;  
}
```
### Benefits
- Code reuse
- Better structure
- Improved readability

## 7. Combined Example

### Objective

Manage users with basic operations.

### Code

```
Set<String> users = {};  
Map<String, Map<String, dynamic>> userData = {};  
  
void addUser(String name, int age) {  
  users.add(name);  
  
  userData[name] = {  
    "age": age  
  };  
}  
  
void printUsers() {  
  for (var user in users) {  
    print("Name: $user, Age: ${userData[user]?["age"]}");  
  }  
}
  
void main() {  
  addUser("Aman", 22);  
  addUser("Ravi", 24);  
  addUser("Aman", 22); // duplicate  
  
  printUsers();  
}
```

## 8. Practice Problems

1. Create a List of integers and print all even numbers.
2. Remove duplicates from a List using Set.
3. Create a Map for a student with name, marks, and grade.
4. Write a function to find the maximum number in a List.
5. Iterate over a Map and print all key-value pairs.