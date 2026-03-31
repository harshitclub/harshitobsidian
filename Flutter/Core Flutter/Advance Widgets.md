# 1. FutureBuilder

## What is it?

`FutureBuilder` is used when:  
You want to **load data once (async)** — like API calls, database fetch.

It handles 3 states:
- Loading
- Success
- Error
## Full Example (Copy → Paste → Run)

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  Future<String> fetchData() async {  
    await Future.delayed(Duration(seconds: 2));  
    return "Data Loaded Successfully!";  
  }  
  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: Scaffold(  
        appBar: AppBar(title: Text("FutureBuilder Example")),  
        body: Center(  
          child: FutureBuilder<String>(  
            future: fetchData(),  
            builder: (context, snapshot) {  
              if (snapshot.connectionState == ConnectionState.waiting) {  
                return CircularProgressIndicator();  
              } else if (snapshot.hasError) {  
                return Text("Error: ${snapshot.error}");  
              } else {  
                return Text(snapshot.data ?? "");  
              }  
            },  
          ),  
        ),  
      ),  
    );  
  }  
}
```
# 2. StreamBuilder

## What is it?

`StreamBuilder` is used when:  
You want **continuous real-time data updates**

Example:
- Chat apps
- Live stock prices
- Firebase real-time data
## Full Example

```
import 'dart:async';  
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  Stream<int> counterStream() async* {  
    for (int i = 1; i <= 10; i++) {  
      await Future.delayed(Duration(seconds: 1));  
      yield i;  
    }  
  }  
  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(  
      home: Scaffold(  
        appBar: AppBar(title: Text("StreamBuilder Example")),  
        body: Center(  
          child: StreamBuilder<int>(  
            stream: counterStream(),  
            builder: (context, snapshot) {  
              if (!snapshot.hasData) {  
                return CircularProgressIndicator();  
              }  
              return Text(  
                "Value: ${snapshot.data}",  
                style: TextStyle(fontSize: 24),  
              );  
            },  
          ),  
        ),  
      ),  
    );  
  }  
}
```
# 3. Hero Animation

## What is it?

`Hero` is used for:  
**Smooth transition animation between screens**

Example:
- Instagram image click → full screen animation
## Full Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(home: FirstScreen());  
  }  
}  
  
class FirstScreen extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
      appBar: AppBar(title: Text("Hero Example")),  
      body: Center(  
        child: GestureDetector(  
          onTap: () {  
            Navigator.push(  
              context,  
              MaterialPageRoute(builder: (_) => SecondScreen()),  
            );  
          },  
          child: Hero(  
            tag: "imageHero",  
            child: Image.network(  
              "https://picsum.photos/200",  
              width: 100,  
            ),  
          ),  
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
      body: Center(  
        child: Hero(  
          tag: "imageHero",  
          child: Image.network("https://picsum.photos/200"),  
        ),  
      ),  
    );  
  }  
}
```
# 4. TabBar + TabBarView

## What is it?

Used for:  
**Top navigation tabs (like WhatsApp, Chrome tabs)**
## Full Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(home: TabExample());  
  }  
}  
  
class TabExample extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return DefaultTabController(  
      length: 3,  
      child: Scaffold(  
        appBar: AppBar(  
          title: Text("TabBar Example"),  
          bottom: TabBar(  
            tabs: [  
              Tab(icon: Icon(Icons.home)),  
              Tab(icon: Icon(Icons.search)),  
              Tab(icon: Icon(Icons.person)),  
            ],  
          ),  
        ),  
        body: TabBarView(  
          children: [  
            Center(child: Text("Home Tab")),  
            Center(child: Text("Search Tab")),  
            Center(child: Text("Profile Tab")),  
          ],  
        ),  
      ),  
    );  
  }  
}
```
# 5. BottomNavigationBar

## What is it?

Used for:  
**Bottom navigation (like Instagram, YouTube)**
## Full Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(home: BottomNavExample());  
  }  
}  
  
class BottomNavExample extends StatefulWidget {  
  @override  
  _BottomNavExampleState createState() => _BottomNavExampleState();  
}  
  
class _BottomNavExampleState extends State<BottomNavExample> {  
  int currentIndex = 0;  
  
  final screens = [  
    Center(child: Text("Home")),  
    Center(child: Text("Search")),  
    Center(child: Text("Profile")),  
  ];  
  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
      appBar: AppBar(title: Text("Bottom Navigation")),  
      body: screens[currentIndex],  
      bottomNavigationBar: BottomNavigationBar(  
        currentIndex: currentIndex,  
        onTap: (index) {  
          setState(() {  
            currentIndex = index;  
          });  
        },  
        items: [  
          BottomNavigationBarItem(icon: Icon(Icons.home), label: "Home"),  
          BottomNavigationBarItem(icon: Icon(Icons.search), label: "Search"),  
          BottomNavigationBarItem(icon: Icon(Icons.person), label: "Profile"),  
        ],  
      ),  
    );  
  }  
}
```
# 6. Slivers (VERY IMPORTANT FOR REAL APPS)

## What is it?

Slivers are used for:  
**Advanced scrolling effects**

Example:
- Collapsing AppBar
- Instagram-like scrolling
- Flexible headers
## Full Example

```
import 'package:flutter/material.dart';  
  
void main() {  
  runApp(MyApp());  
}  
  
class MyApp extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return MaterialApp(home: SliverExample());  
  }  
}  
  
class SliverExample extends StatelessWidget {  
  @override  
  Widget build(BuildContext context) {  
    return Scaffold(  
      body: CustomScrollView(  
        slivers: [  
          SliverAppBar(  
            expandedHeight: 200,  
            pinned: true,  
            flexibleSpace: FlexibleSpaceBar(  
              title: Text("Sliver AppBar"),  
              background: Image.network(  
                "https://picsum.photos/500",  
                fit: BoxFit.cover,  
              ),  
            ),  
          ),  
  
          SliverList(  
            delegate: SliverChildBuilderDelegate(  
              (context, index) => ListTile(  
                title: Text("Item $index"),  
              ),  
              childCount: 20,  
            ),  
          ),  
        ],  
      ),  
    );  
  }  
}
```