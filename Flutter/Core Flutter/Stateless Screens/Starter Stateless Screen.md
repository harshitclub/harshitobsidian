```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

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

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Student Info"),
        centerTitle: true,
      ),
      body: Padding(
        padding: const EdgeInsets.all(16),
        child: Column(
          children: [

            Row(
              children: const [
                Icon(Icons.person),
                SizedBox(width: 10),
                Text(
                  "Harshit Kumar",
                  style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
                ),
              ],
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

            const SizedBox(height: 20),

            Row(
              children: [
                Expanded(
                  child: Container(
                    padding: const EdgeInsets.all(12),
                    color: Colors.purple.shade50,
                    child: const Center(child: Text("Flutter")),
                  ),
                ),
                const SizedBox(width: 10),
                Expanded(
                  child: Container(
                    padding: const EdgeInsets.all(12),
                    color: Colors.red.shade50,
                    child: const Center(child: Text("Dart")),
                  ),
                ),
              ],
            ),

            const SizedBox(height: 20),

            const Text(
              "Keep learning and building projects daily.",
              textAlign: TextAlign.center,
            ),
          ],
        ),
      ),
    );
  }
}
```

# Notes

# 1. Entry Point of App

```
void main() {  
  runApp(const MyApp());  
}
```
### Explanation

- `main()` is the starting point of every Flutter app
- `runApp()` tells Flutter to render the UI
- `MyApp` becomes the root widget of the app
# 2. Root Widget (MyApp)

```
class MyApp extends StatelessWidget
```
### Explanation

- This is a **StatelessWidget**
- It does not hold any changing data
- It only returns UI
## MaterialApp

```
MaterialApp(  
  home: HomeScreen(),  
)
```
### Purpose

- Provides basic app structure
- Enables Material Design (UI system)
- Connects your main screen (`HomeScreen`)
# 3. HomeScreen (Main UI)

```
class HomeScreen extends StatelessWidget
```
### Explanation

- This is your main screen
- It is stateless → UI does not change dynamically
# 4. Scaffold (Page Structure)

```
Scaffold(  
  appBar: AppBar(...),  
  body: ...  
)
```
### Purpose

Scaffold provides:

- AppBar → top header
- Body → main content
- Overall page structure
# 5. AppBar (Header)

```
AppBar(  
  title: Text("Student Info"),  
  centerTitle: true,  
)
```
### Explanation

- Displays title at top
- `centerTitle: true` centers the text
# 6. Padding (Spacing)

```
Padding(  
  padding: EdgeInsets.all(16),  
)
```
### Purpose

- Adds space around the content
- Prevents UI from touching screen edges
# 7. Column (Vertical Layout)

```
Column(  
  children: []  
)
```
### Explanation

- Arranges widgets vertically (top to bottom)
- Main layout structure of this screen
# 8. Row (Horizontal Layout)

```
Row(  
  children: []  
)
```
### Used For

- Profile section (icon + name)
- Skills section (Flutter + Dart)
# 9. Icon + Text (Basic UI)

```
Icon(Icons.person)  
Text("Harshit Kumar")
```
### Purpose

- Icon → visual representation
- Text → displays information
# 10. SizedBox (Spacing)

```
SizedBox(height: 20)
```
### Purpose

- Adds space between widgets
- Keeps UI clean and readable
# 11. Container (Box + Styling)

```
Container(  
  padding: EdgeInsets.all(12),  
  color: Colors.blue.shade50,  
  child: Text(...)  
)
```
### Explanation

Container is used for:

- Background color
- Padding (inner spacing)
- Layout control
# 12. Expanded (Flexible Space)

```
Expanded(  
  child: Container(...)  
)
```
### Purpose

- Makes widget take available space
- Used inside Row to divide space equally
# 13. Center (Alignment)

```
Center(child: Text("Flutter"))
```
### Purpose

- Centers content inside a widget
# 14. Final Text (Message)

```
Text(  
  "Keep learning and building projects daily.",  
  textAlign: TextAlign.center,  
)
```
### Explanation

- Displays message
- `textAlign: center` centers the text