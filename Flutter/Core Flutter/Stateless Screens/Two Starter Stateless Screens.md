```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

/// ROOT APP
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: HomeScreen(),
    );
  }
}

/// ================= HOME SCREEN =================
class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Home Screen"),
        centerTitle: true,
      ),

      body: Padding(
        padding: const EdgeInsets.all(16),
        child: Column(
          children: [

            const Text(
              "Student Dashboard",
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),

            const SizedBox(height: 20),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.blue.shade50,
              child: const Text("College: Tulas Institute"),
            ),

            const SizedBox(height: 10),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.green.shade50,
              child: const Text("Course: BCA"),
            ),

            const SizedBox(height: 10),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.orange.shade50,
              child: const Text("Year: 2nd"),
            ),

            const SizedBox(height: 30),

            ElevatedButton(
              onPressed: () {

                /// NAVIGATE TO SECOND SCREEN
                Navigator.push(
                  context,
                  MaterialPageRoute(
                    builder: (context) => const DetailScreen(),
                  ),
                );
              },
              child: const Text("Go to Details"),
            ),
          ],
        ),
      ),
    );
  }
}

/// ================= DETAIL SCREEN =================
class DetailScreen extends StatelessWidget {
  const DetailScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Detail Screen"),
        centerTitle: true,
      ),

      body: Padding(
        padding: const EdgeInsets.all(16),
        child: Column(
          children: [

            const Text(
              "Training Information",
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),

            const SizedBox(height: 20),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.purple.shade50,
              child: const Text("Flutter Development"),
            ),

            const SizedBox(height: 10),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.red.shade50,
              child: const Text("Dart Programming"),
            ),

            const SizedBox(height: 10),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.teal.shade50,
              child: const Text("API Integration"),
            ),

            const SizedBox(height: 30),

            ElevatedButton(
              onPressed: () {

                /// GO BACK TO PREVIOUS SCREEN
                Navigator.pop(context);
              },
              child: const Text("Go Back"),
            ),
          ],
        ),
      ),
    );
  }
}
```

# Flutter Navigation Basics (Stateless Approach)

# 1. Introduction to Navigation

Navigation in Flutter allows moving from one screen to another.

In simple terms:

- Screen = Widget
- Navigation = Moving between widgets

Flutter uses a **stack-based navigation system**.
# 2. Navigation Stack Concept

Flutter manages screens using a stack (like a pile of pages).

```
HomeScreen  
   ↓ push  
DetailScreen  
   ↓ pop  
HomeScreen
```

- `push` → adds a new screen on top
- `pop` → removes the current screen
# 3. Basic Navigation Methods

## 3.1 Navigate to Next Screen (Push)

```
Navigator.push(  
  context,  
  MaterialPageRoute(  
    builder: (context) => const DetailScreen(),  
  ),  
);
```
### Explanation

- `Navigator.push` → moves to a new screen
- `context` → current position in widget tree
- `MaterialPageRoute` → defines transition
- `builder` → returns the next screen
## 3.2 Go Back (Pop)

```
Navigator.pop(context);
```
### Explanation

- Removes current screen
- Returns to previous screen
# 4. Understanding BuildContext

`BuildContext` is required for navigation.

It represents:

- Location of widget in widget tree
- Access point for navigation and theme

Example usage:

```
Navigator.push(context, ...);
```

Without context, navigation cannot work.
# 5. Complete Flow Example

## HomeScreen Button

```
ElevatedButton(  
  onPressed: () {  
    Navigator.push(  
      context,  
      MaterialPageRoute(  
        builder: (context) => const DetailScreen(),  
      ),  
    );  
  },  
  child: const Text("Go to Details"),  
)
```
## DetailScreen Button

```
ElevatedButton(  
  onPressed: () {  
    Navigator.pop(context);  
  },  
  child: const Text("Go Back"),  
)
```
# 6. Structure of Navigation

```
main()  
  ↓  
MaterialApp  
  ↓  
HomeScreen  
  ↓ (push)  
DetailScreen
```
# 7. Important Widgets Used

|Widget|Purpose|
|---|---|
|MaterialApp|Root app configuration|
|Scaffold|Screen layout|
|Navigator|Handles navigation|
|MaterialPageRoute|Screen transition|
|ElevatedButton|Trigger navigation|

# 8. Key Points to Remember

1. Navigation requires `BuildContext`
2. Always use `Navigator.push` to go forward
3. Always use `Navigator.pop` to go back
4. Flutter follows stack-based navigation
5. Each screen is a widget

---
# Separating The Pages
# **Step 1: Create a New File**

Inside `lib/` folder:

👉 Create a new file:

```
detail_screen.dart
```
# **Step 2: Move DetailScreen Code**

Paste this inside `detail_screen.dart`:

```
import 'package:flutter/material.dart';

class DetailScreen extends StatelessWidget {
  const DetailScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Detail Screen"),
        centerTitle: true,
      ),
      body: Padding(
        padding: const EdgeInsets.all(16),
        child: Column(
          children: [

            const Text(
              "Training Information",
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),

            const SizedBox(height: 20),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.purple.shade50,
              child: const Text("Flutter Development"),
            ),

            const SizedBox(height: 10),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.red.shade50,
              child: const Text("Dart Programming"),
            ),

            const SizedBox(height: 10),

            Container(
              padding: const EdgeInsets.all(12),
              width: double.infinity,
              color: Colors.teal.shade50,
              child: const Text("API Integration"),
            ),

            const SizedBox(height: 30),

            ElevatedButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: const Text("Go Back"),
            ),
          ],
        ),
      ),
    );
  }
}
```
# **Step 3: Update HomeScreen File**

In your main file (where HomeScreen exists):

👉 Add this import at the top:

```
import 'detail_screen.dart';
```
# **Step 4: Use DetailScreen**

Your navigation code stays SAME:

```
Navigator.push(  
  context,  
  MaterialPageRoute(  
    builder: (context) => const DetailScreen(),  
  ),  
);
```
# **How Import Works**

```
import 'detail_screen.dart';
```

👉 Means:

- “Bring code from this file”
- Now you can use `DetailScreen`
# **Final Project Structure**

```
lib/  
 ├── main.dart  
 └── detail_screen.dart
```