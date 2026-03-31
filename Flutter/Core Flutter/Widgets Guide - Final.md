# 1. CORE STRUCTURE WIDGETS

## MaterialApp, Scaffold, AppBar, Body

These are the **foundation of every app**
### Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      title: 'Basic Structure',  
      home: Scaffold(  
        appBar: AppBar(  
          title: Text('AppBar Example'),  
        ),  
        body: Center(  
          child: Text('Hello Flutter'),  
        ),  
      ),  
    );  
  }  
}
```
# 2. BASIC UI WIDGETS

## Text, Icon, Image

### Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: Scaffold(  
        appBar: AppBar(title: Text("Basic Widgets")),  
        body: Column(  
          mainAxisAlignment: MainAxisAlignment.center,  
          children: [  
            Text("This is Text Widget", style: TextStyle(fontSize: 20)),  
  
            Icon(Icons.star, size: 40, color: Colors.blue),  
  
            Image.network(  
              "https://picsum.photos/200",  
              height: 100,  
            ),  
          ],  
        ),  
      ),  
    );  
  }  
}
```
# 3. LAYOUT WIDGETS (MOST IMPORTANT)

## Row, Column, Container, Expanded, SizedBox

### Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: Scaffold(  
        appBar: AppBar(title: Text("Layout Widgets")),  
        body: Column(  
          children: [  
            Container(  
              height: 100,  
              color: Colors.red,  
              child: Center(child: Text("Container")),  
            ),  
  
            Row(  
              children: [  
                Expanded(child: Container(height: 50, color: Colors.green)),  
                Expanded(child: Container(height: 50, color: Colors.blue)),  
              ],  
            ),  
  
            SizedBox(height: 20),  
  
            Text("Spacing using SizedBox"),  
          ],  
        ),  
      ),  
    );  
  }  
}
```
# 4. SCROLLABLE WIDGETS

## ListView, GridView, SingleChildScrollView

### Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  final List<String> items = List.generate(20, (index) => "Item $index");  
  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: Scaffold(  
        appBar: AppBar(title: Text("ListView Example")),  
        body: ListView.builder(  
          itemCount: items.length,  
          itemBuilder: (context, index) {  
            return ListTile(  
              title: Text(items[index]),  
              leading: Icon(Icons.person),  
            );  
          },  
        ),  
      ),  
    );  
  }  
}
```
# 5. INPUT WIDGETS

## TextField, ElevatedButton, Checkbox, Switch

### Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatefulWidget {  
  @override  
  _MyAppState createState() => _MyAppState();  
}  
  
class _MyAppState extends State<MyApp> {  
  bool isChecked = false;  
  bool isSwitchOn = false;  
  String text = "";  
  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: Scaffold(  
        appBar: AppBar(title: Text("Input Widgets")),  
        body: Padding(  
          padding: EdgeInsets.all(20),  
          child: Column(  
            children: [  
              TextField(  
                onChanged: (value) {  
                  setState(() {  
                    text = value;  
                  });  
                },  
              ),  
  
              ElevatedButton(  
                onPressed: () {  
                  print("Button Pressed");  
                },  
                child: Text("Click Me"),  
              ),  
  
              Checkbox(  
                value: isChecked,  
                onChanged: (value) {  
                  setState(() {  
                    isChecked = value!;  
                  });  
                },  
              ),  
  
              Switch(  
                value: isSwitchOn,  
                onChanged: (value) {  
                  setState(() {  
                    isSwitchOn = value;  
                  });  
                },  
              ),  
  
              Text("You typed: $text"),  
            ],  
          ),  
        ),  
      ),  
    );  
  }  
}
```
# 6. STYLING WIDGETS

## Padding, Align, Center, DecoratedBox

### Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: Scaffold(  
        appBar: AppBar(title: Text("Styling Widgets")),  
        body: Center(  
          child: Padding(  
            padding: EdgeInsets.all(20),  
            child: Container(  
              decoration: BoxDecoration(  
                color: Colors.orange,  
                borderRadius: BorderRadius.circular(10),  
              ),  
              padding: EdgeInsets.all(20),  
              child: Text("Styled Container"),  
            ),  
          ),  
        ),  
      ),  
    );  
  }  
}
```
# 7. NAVIGATION WIDGETS

## Navigator, Routes

### Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: FirstScreen(),  
    );  
  }  
}  
  
class FirstScreen extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
      appBar: AppBar(title: Text("First Screen")),  
      body: Center(  
        child: ElevatedButton(  
          child: Text("Go to Second Screen"),  
          onPressed: () {  
            Navigator.push(  
              context,  
              MaterialPageRoute(builder: (_) => SecondScreen()),  
            );  
          },  
        ),  
      ),  
    );  
  }  
}  
  
class SecondScreen extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
      appBar: AppBar(title: Text("Second Screen")),  
      body: Center(child: Text("Welcome")),  
    );  
  }  
}
```
# 8. ADVANCED (IMPORTANT REAL-WORLD)

## Stack, Positioned

### Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: Scaffold(  
        body: Stack(  
          children: [  
            Container(color: Colors.blue),  
  
            Positioned(  
              top: 100,  
              left: 50,  
              child: Container(  
                width: 100,  
                height: 100,  
                color: Colors.red,  
              ),  
            ),  
          ],  
        ),  
      ),  
    );  
  }  
}
```