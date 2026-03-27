### **The Base App Template**

Put this at the very top of your `main.dart` file. Leave it there, and just swap out the `home:` property to test the examples below.

```
import 'package:flutter/material.dart';

void main() {
  runApp(const MaterialApp(
    debugShowCheckedModeBanner: false,
    home: ColumnExample(), // <--- CHANGE THIS NAME TO TEST DIFFERENT WIDGETS
  ));
}
```
### **Phase 1: The Invisible Structure (Aligning Boxes)**

#### **1. `Column` (Vertical Stacking)**

Stacks widgets from top to bottom.

```
class ColumnExample extends StatelessWidget {
  const ColumnExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Column Example')),
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center, // Centers vertically
        crossAxisAlignment: CrossAxisAlignment.center, // Centers horizontally
        children: [
          Container(height: 50, width: 50, color: Colors.red),
          const SizedBox(height: 10), // Spacing
          Container(height: 50, width: 50, color: Colors.blue),
          const SizedBox(height: 10),
          Container(height: 50, width: 50, color: Colors.green),
        ],
      ),
    );
  }
}
```
#### **2. `Row` (Horizontal Stacking)**

Lays out widgets from left to right.

```
class RowExample extends StatelessWidget {
  const RowExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Row Example')),
      body: Row(
        mainAxisAlignment: MainAxisAlignment.spaceEvenly, // Spaces them out equally
        children: [
          Container(height: 50, width: 50, color: Colors.red),
          Container(height: 50, width: 50, color: Colors.blue),
          Container(height: 50, width: 50, color: Colors.green),
        ],
      ),
    );
  }
}
```
#### **3. `Expanded` (The Space Filler)**

Forces a widget to stretch and consume all remaining empty space inside a Row or Column.

```
class ExpandedExample extends StatelessWidget {
  const ExpandedExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Expanded Example')),
      body: Row(
        children: [
          Container(height: 50, width: 50, color: Colors.red),
          // This blue box will stretch to fill all the middle space
          Expanded(
            child: Container(height: 50, color: Colors.blue),
          ),
          Container(height: 50, width: 50, color: Colors.green),
        ],
      ),
    );
  }
}
```
#### **4. `Stack` & `Positioned` (Z-Index Layering)**

`Stack` places widgets on top of each other. `Positioned` lets you pin a widget to exact coordinates inside that Stack.

```
class StackExample extends StatelessWidget {
  const StackExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Stack & Positioned')),
      body: Center(
        child: Stack(
          children: [
            // Bottom Layer
            Container(height: 200, width: 200, color: Colors.grey[300]),
            // Middle Layer (Centered)
            const Center(child: Text('Background Box', style: TextStyle(fontSize: 20))),
            // Top Layer (Pinned to bottom right)
            Positioned(
              bottom: 10,
              right: 10,
              child: Container(height: 50, width: 50, color: Colors.red),
            ),
          ],
        ),
      ),
    );
  }
}
```
### **Phase 2: The Canvas (The "divs")**

#### **5. `Container` (The Universal Box)**

Used for backgrounds, borders, padding, and shapes.

```
class ContainerExample extends StatelessWidget {
  const ContainerExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Container Example')),
      body: Center(
        child: Container(
          height: 150,
          width: 250,
          alignment: Alignment.center,
          decoration: BoxDecoration(
            color: Colors.deepPurple,
            borderRadius: BorderRadius.circular(20),
            boxShadow: const [
              BoxShadow(color: Colors.black45, blurRadius: 10, offset: Offset(5, 5))
            ],
          ),
          child: const Text('Beautiful Box', style: TextStyle(color: Colors.white, fontSize: 24)),
        ),
      ),
    );
  }
}
```
### **Phase 3: The Content (What the user sees)**

#### **6. `Text`, `Icon`, and `Image`**

The core visual elements.

```
class ContentExample extends StatelessWidget {
  const ContentExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Content Example')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Icon(Icons.rocket_launch, size: 80, color: Colors.orange),
            const SizedBox(height: 20),
            const Text(
              'Houston, we have liftoff!',
              style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold, letterSpacing: 2),
            ),
            const SizedBox(height: 20),
            ClipRRect(
              borderRadius: BorderRadius.circular(100),
              child: Image.network(
                'https://images.unsplash.com/photo-1451187580459-43490279c0fa?auto=format&fit=crop&w=200&q=80',
                height: 150,
                width: 150,
                fit: BoxFit.cover,
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```
### **Phase 4: Scrolling & Spacing**

#### **7. `Padding`**

Adds breathing room around a widget without using a heavy `Container`.

```
class PaddingExample extends StatelessWidget {
  const PaddingExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Padding Example')),
      body: Padding(
        padding: const EdgeInsets.all(40.0), // Adds 40px of space on all sides
        child: Container(color: Colors.teal, child: const Center(child: Text('I am padded!'))),
      ),
    );
  }
}
```
#### **8. `ListView.builder` (Efficient Scrolling)**

The absolute best way to render a long list of data statelessly.

```
class ListViewExample extends StatelessWidget {
  const ListViewExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('ListView Example')),
      body: ListView.builder(
        itemCount: 20, // Loops 20 times
        itemBuilder: (context, index) {
          return Card(
            margin: const EdgeInsets.all(8),
            child: ListTile(
              leading: CircleAvatar(child: Text('${index + 1}')),
              title: Text('List Item Number ${index + 1}'),
              trailing: const Icon(Icons.arrow_forward_ios),
            ),
          );
        },
      ),
    );
  }
}
```
### **Phase 5: Interaction**

#### **9. `ElevatedButton` & `GestureDetector`**

Making things clickable. Even statelessly, they can trigger print statements or standard navigation.

```
class InteractionExample extends StatelessWidget {
  const InteractionExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Interaction Example')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            ElevatedButton(
              style: ElevatedButton.styleFrom(backgroundColor: Colors.indigo, padding: const EdgeInsets.symmetric(horizontal: 40, vertical: 15)),
              onPressed: () => print('Standard Button Clicked!'),
              child: const Text('Click Me', style: TextStyle(color: Colors.white)),
            ),
            const SizedBox(height: 40),
            GestureDetector(
              onTap: () => print('Custom Container Clicked!'),
              child: Container(
                padding: const EdgeInsets.all(20),
                decoration: BoxDecoration(color: Colors.amber, borderRadius: BorderRadius.circular(12)),
                child: const Text('I am a clickable custom box!'),
              ),
            )
          ],
        ),
      ),
    );
  }
}
```
### **THE MASTER PRACTICAL EXAMPLE**

Now, let's combine _every single widget_ you just learned into one gorgeous, cohesive layout. This is a real-world "Course Detail" page.

Just copy this, change your `home:` property to `MasterLayoutExample()`, and run it.

```
class MasterLayoutExample extends StatelessWidget {
  const MasterLayoutExample({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: const Color(0xFFF8FAFC),
      // 1. SCAFFOLD & APPBAR
      appBar: AppBar(
        title: const Text('Course Details', style: TextStyle(color: Colors.black)),
        backgroundColor: Colors.white,
        elevation: 0,
        iconTheme: const IconThemeData(color: Colors.black),
      ),
      // 2. SINGLE CHILDS CROLL VIEW (To prevent overflow)
      body: SingleChildScrollView(
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // 3. STACK & POSITIONED (Header Image with Category Badge)
            Stack(
              children: [
                // 4. IMAGE
                Image.network(
                  'https://images.unsplash.com/photo-1555066931-4365d14bab8c?auto=format&fit=crop&w=800&q=80',
                  height: 250,
                  width: double.infinity,
                  fit: BoxFit.cover,
                ),
                Positioned(
                  top: 16,
                  right: 16,
                  child: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 12, vertical: 6),
                    decoration: BoxDecoration(color: Colors.blueAccent, borderRadius: BorderRadius.circular(20)),
                    child: const Text('BESTSELLER', style: TextStyle(color: Colors.white, fontWeight: FontWeight.bold, fontSize: 12)),
                  ),
                ),
              ],
            ),
            
            // 5. PADDING
            Padding(
              padding: const EdgeInsets.all(24.0),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  // 6. TEXT
                  const Text(
                    'Advanced Flutter Layouts',
                    style: TextStyle(fontSize: 28, fontWeight: FontWeight.bold),
                  ),
                  const SizedBox(height: 10), // 7. SIZED BOX
                  
                  // 8. ROW (Ratings and Students)
                  Row(
                    children: const [
                      Icon(Icons.star, color: Colors.amber, size: 20),
                      SizedBox(width: 5),
                      Text('4.9', style: TextStyle(fontWeight: FontWeight.bold, fontSize: 16)),
                      SizedBox(width: 15),
                      Icon(Icons.people, color: Colors.grey, size: 20),
                      SizedBox(width: 5),
                      Text('12,400 Students', style: TextStyle(color: Colors.grey)),
                    ],
                  ),
                  
                  const SizedBox(height: 30),
                  const Text('Course Contents', style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold)),
                  const SizedBox(height: 16),

                  // 9. CONTAINER (A custom card for the curriculum)
                  Container(
                    decoration: BoxDecoration(
                      color: Colors.white,
                      borderRadius: BorderRadius.circular(16),
                      border: Border.all(color: Colors.grey.shade200),
                    ),
                    // 10. LISTVIEW (Using shrinkWrap so it plays nice inside a Column)
                    child: ListView.separated(
                      shrinkWrap: true, // Crucial when putting a ListView inside a ScrollView
                      physics: const NeverScrollableScrollPhysics(), // Disables inner scrolling
                      itemCount: 3,
                      separatorBuilder: (context, index) => const Divider(height: 1),
                      itemBuilder: (context, index) {
                        List<String> modules = ['Thinking in Widgets', 'Mastering Flexbox', 'Z-Index and Stacks'];
                        return ListTile(
                          leading: Container(
                            padding: const EdgeInsets.all(8),
                            decoration: BoxDecoration(color: Colors.blue.withOpacity(0.1), shape: BoxShape.circle),
                            // 11. ICON
                            child: const Icon(Icons.play_arrow, color: Colors.blue),
                          ),
                          title: Text(modules[index], style: const TextStyle(fontWeight: FontWeight.w600)),
                          subtitle: const Text('15 mins'),
                        );
                      },
                    ),
                  ),

                  const SizedBox(height: 40),

                  // 12. ROW & EXPANDED (Bottom action buttons)
                  Row(
                    children: [
                      // 13. GESTURE DETECTOR (Custom bookmark button)
                      GestureDetector(
                        onTap: () => print('Bookmarked!'),
                        child: Container(
                          padding: const EdgeInsets.all(16),
                          decoration: BoxDecoration(
                            border: Border.all(color: Colors.grey.shade300),
                            borderRadius: BorderRadius.circular(12),
                          ),
                          child: const Icon(Icons.bookmark_border),
                        ),
                      ),
                      const SizedBox(width: 16),
                      // EXPANDED (Forces the Enroll button to take the remaining width)
                      Expanded(
                        // 14. ELEVATED BUTTON
                        child: ElevatedButton(
                          onPressed: () => print('Enrolled!'),
                          style: ElevatedButton.styleFrom(
                            backgroundColor: Colors.blueAccent,
                            padding: const EdgeInsets.symmetric(vertical: 16),
                            shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)),
                          ),
                          child: const Text('Enroll Now - $49', style: TextStyle(fontSize: 18, color: Colors.white, fontWeight: FontWeight.bold)),
                        ),
                      ),
                    ],
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```