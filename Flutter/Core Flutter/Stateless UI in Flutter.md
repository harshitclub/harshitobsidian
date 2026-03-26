# 1. Code Flow in a Stateless Flutter App

Before learning widgets, you must understand how Flutter renders UI.
## Basic Flow

```
void main() {  
  runApp(const MyApp());  
}
```
### Explanation

1. `main()` is the entry point.
2. `runApp()` inflates the given widget (`MyApp`).
3. Flutter builds a **widget tree** from top to bottom.

## Root Structure

```
MaterialApp  
  └── HomeScreen  
        └── Scaffold  
              ├── AppBar  
              └── Body
```
### Key Idea

- Flutter UI = **Tree of Widgets**
- Each widget describes a part of UI
- Stateless widgets are **pure functions of UI**
# 2. StatelessWidget (Foundation)

## Definition

A `StatelessWidget` is immutable and does not change over time.

```
class MyWidget extends StatelessWidget {  
  const MyWidget({super.key});  
  
  @override  
  Widget build(BuildContext context) {  
    return const Text("Hello");  
  }  
}
```
## Key Properties

- No internal state
- UI depends only on input
- Rebuild happens only when parent changes
# 3. Core Structural Widgets

These define the **layout skeleton**.

## 3.1 Scaffold

Provides basic screen structure.

```
Scaffold(  
  appBar: AppBar(title: Text("Title")),  
  body: Center(child: Text("Content")),  
)
```
### Important Properties

- `appBar`
- `body`
- `floatingActionButton`
- `backgroundColor`

## 3.2 AppBar

Top navigation bar.

```
AppBar(  
  title: Text("Header"),  
  centerTitle: true,  
  backgroundColor: Colors.blue,  
  elevation: 0,  
)
```
### Styling Options

- `title`
- `centerTitle`
- `backgroundColor`
- `actions`
- `elevation`

## 3.3 Center

Centers its child.

```
Center(  
  child: Text("Centered"),  
)
```

# 4. Layout Widgets (Very Important)

These control positioning.
## 4.1 Column (Vertical Layout)

```
Column(  
  mainAxisAlignment: MainAxisAlignment.center,  
  crossAxisAlignment: CrossAxisAlignment.start,  
  children: const [  
    Text("A"),  
    Text("B"),  
  ],  
)
```
### Properties

- `mainAxisAlignment` → vertical alignment
- `crossAxisAlignment` → horizontal alignment
- `mainAxisSize` → min / max
## 4.2 Row (Horizontal Layout)

```
Row(  
  mainAxisAlignment: MainAxisAlignment.spaceBetween,  
  children: const [  
    Text("Left"),  
    Text("Right"),  
  ],  
)
```
## 4.3 Expanded

Takes remaining space.

```
Row(  
  children: const [  
    Expanded(child: Text("Flexible")),  
    Text("Fixed"),  
  ],  
)
```
## 4.4 SizedBox

Adds spacing or fixed size.

```
SizedBox(height: 20)  
SizedBox(width: 100, height: 50)
```
## 4.5 Padding

Adds inner spacing.

```
Padding(  
  padding: EdgeInsets.all(16),  
  child: Text("Padded"),  
)
```
## 4.6 Container (Styling Box)

Most flexible widget.

```
Container(  
  padding: EdgeInsets.all(16),  
  margin: EdgeInsets.all(10),  
  decoration: BoxDecoration(  
    color: Colors.white,  
    borderRadius: BorderRadius.circular(10),  
    boxShadow: [  
      BoxShadow(  
        blurRadius: 10,  
        color: Colors.black12,  
      ),  
    ],  
  ),  
  child: Text("Styled Box"),  
)
```
### Styling Capabilities

- `padding`
- `margin`
- `color`
- `decoration`
- `alignment`
- `constraints`
# 5. Content Widgets

## 5.1 Text

```
Text(  
  "Hello Flutter",  
  style: TextStyle(  
    fontSize: 18,  
    fontWeight: FontWeight.bold,  
    color: Colors.black,  
    letterSpacing: 1,  
  ),  
)
```
### Styling Options

- `fontSize`
- `fontWeight`
- `color`
- `letterSpacing`
- `height` (line height)
## 5.2 Icon

```
Icon(Icons.home, size: 30, color: Colors.blue)
```
## 5.3 Image

```
Image.network("https://example.com/image.png")
```

Other types:

- `Image.asset()`
- `Image.file()`
# 6. Card and Material Design Widgets

## 6.1 Card

```
Card(  
  elevation: 3,  
  shape: RoundedRectangleBorder(  
    borderRadius: BorderRadius.circular(12),  
  ),  
  child: Padding(  
    padding: EdgeInsets.all(16),  
    child: Text("Card Content"),  
  ),  
)
```

# 7. Alignment and Positioning

## 7.1 Align

```
Align(  
  alignment: Alignment.centerRight,  
  child: Text("Right aligned"),  
)
```
## 7.2 Spacer

Used inside Row/Column

```
Row(  
  children: const [  
    Text("Left"),  
    Spacer(),  
    Text("Right"),  
  ],  
)
```
# 8. Theming and Styling

## ThemeData

```
theme: ThemeData(  
  colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue),  
  textTheme: TextTheme(  
    bodyMedium: TextStyle(fontSize: 16),  
  ),  
)
```
## Using Theme

```
Text(  
  "Hello",  
  style: Theme.of(context).textTheme.bodyMedium,  
)
```

# Mental Model

Think like this:

```
Scaffold  
  └── body (ONE widget)  
         └── Column (container)  
                ├── Child 1  
                ├── Child 2  
                └── Child 3
```
# When to use what

| Situation       | Widget   |
| --------------- | -------- |
| Vertical UI     | Column   |
| Horizontal UI   | Row      |
| Scrollable list | ListView |
| Overlay UI      | Stack    |
# 9. Building a Minimal UI Example

## Example: Clean Student Card

```
class StudentCard extends StatelessWidget {  
  const StudentCard({super.key});  
  
  @override  
  Widget build(BuildContext context) {  
    return Center(  
      child: Container(  
        padding: const EdgeInsets.all(20),  
        margin: const EdgeInsets.all(20),  
        decoration: BoxDecoration(  
          color: Colors.white,  
          borderRadius: BorderRadius.circular(12),  
          boxShadow: [  
            BoxShadow(color: Colors.black12, blurRadius: 10),  
          ],  
        ),  
        child: Column(  
          mainAxisSize: MainAxisSize.min,  
          crossAxisAlignment: CrossAxisAlignment.start,  
          children: const [  
            Text(  
              "Tulas Institute",  
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),  
            ),  
            SizedBox(height: 10),  
            Text("Course: BCA"),  
            Text("Year: 2nd"),  
            Text("Training: Flutter & Dart"),  
          ],  
        ),  
      ),  
    );  
  }  
}
```
# 10. Key Principles for Minimal UI

1. Use fewer widgets but structure properly
2. Prefer spacing (`SizedBox`) over complex layouts
3. Use `Container` only when styling is needed
4. Keep hierarchy shallow and readable
5. Reuse patterns consistently
# 11. Common Mistakes

- Overusing `Container` when not needed
- Ignoring alignment properties
- Writing deeply nested UI without structure
- Mixing styling everywhere instead of using themes
# 12. Final Mental Model

Think of Flutter like this:

- UI = Function of data
- Widgets = Building blocks
- Layout = Composition (Row, Column, Container)

You are not “drawing UI” — you are **describing structure**