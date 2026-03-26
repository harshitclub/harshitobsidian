```
import 'package:flutter/material.dart';

/// ================= ENTRY POINT =================  
void main() {  
runApp(const MyApp());  
}  
  
/// ================= ROOT APP =================  
/// This wraps your app with MaterialApp  
class MyApp extends StatelessWidget {  
const MyApp({super.key});  
  
@override  
Widget build(BuildContext context) {  
return const MaterialApp(  
debugShowCheckedModeBanner: false,  
  
/// This is your main screen  
home: HomeScreen(),  
);  
}  
}

/// HomeScreen is a StatelessWidget
/// → No state (no changing data)
/// → Only UI rendering
class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(

      /// Background color of whole screen
      backgroundColor: const Color(0xFFF5F7FB),

      /// ================= HEADER =================
      appBar: AppBar(

        /// Transparent AppBar (no solid color)
        backgroundColor: Colors.transparent,

        /// Removes shadow
        elevation: 0,

        /// Title text
        title: const Text(
          "Dashboard",
          style: TextStyle(color: Colors.black),
        ),

        /// Center align title
        centerTitle: true,
      ),

      /// ================= BODY =================
      /// SingleChildScrollView allows scrolling
      /// → Important when content is large
      body: SingleChildScrollView(
        padding: const EdgeInsets.all(16),

        /// Column arranges children vertically
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [

            /// ---------- PROFILE SECTION ----------
            Container(
              padding: const EdgeInsets.all(16),

              /// Styling using BoxDecoration
              decoration: BoxDecoration(
                color: const Color(0xFFDDEBFF), // pastel blue
                borderRadius: BorderRadius.circular(16),
              ),

              /// Row → horizontal layout
              child: Row(
                children: const [

                  /// Circular profile avatar
                  CircleAvatar(
                    radius: 28,
                    backgroundColor: Colors.white,
                    child: Icon(Icons.person, size: 30),
                  ),

                  SizedBox(width: 12),

                  /// Column → vertical text layout
                  Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      Text(
                        "Hello, Student",
                        style: TextStyle(fontSize: 14),
                      ),
                      SizedBox(height: 4),
                      Text(
                        "Welcome Back",
                        style: TextStyle(
                          fontSize: 18,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                    ],
                  )
                ],
              ),
            ),

            const SizedBox(height: 20),

            /// ---------- COLLEGE INFO CARD ----------
            Container(
              padding: const EdgeInsets.all(16),
              decoration: BoxDecoration(
                color: const Color(0xFFEFF7F6), // light green pastel
                borderRadius: BorderRadius.circular(16),
              ),

              /// Column for multiple text items
              child: const Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Text(
                    "College Information",
                    style: TextStyle(
                      fontSize: 16,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  SizedBox(height: 10),

                  /// Information text
                  Text("College: Tulas Institute"),
                  Text("Course: BCA"),
                  Text("Year: 2nd"),
                  Text("Training: Flutter & Dart"),
                ],
              ),
            ),

            const SizedBox(height: 20),

            /// ---------- STATS SECTION ----------
            /// Row for horizontal cards
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: const [
                _StatCard(title: "Attendance", value: "92%"),
                _StatCard(title: "Assignments", value: "8/10"),
                _StatCard(title: "Projects", value: "3"),
              ],
            ),

            const SizedBox(height: 20),

            /// ---------- COURSE PROGRESS ----------
            Container(
              padding: const EdgeInsets.all(16),
              decoration: BoxDecoration(
                color: const Color(0xFFFFF4E6), // light orange pastel
                borderRadius: BorderRadius.circular(16),
              ),

              /// Column for progress items
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: const [
                  Text(
                    "Course Progress",
                    style: TextStyle(
                      fontSize: 16,
                      fontWeight: FontWeight.bold,
                    ),
                  ),

                  SizedBox(height: 10),

                  /// Custom progress rows
                  _ProgressRow(label: "Flutter", progress: 0.7),
                  SizedBox(height: 8),
                  _ProgressRow(label: "Dart", progress: 0.6),
                ],
              ),
            ),

            const SizedBox(height: 20),

            /// ---------- TRAINING SECTION ----------
            Container(
              padding: const EdgeInsets.all(16),
              decoration: BoxDecoration(
                color: const Color(0xFFEDE7FF), // light purple pastel
                borderRadius: BorderRadius.circular(16),
              ),

              child: const Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Text(
                    "Training Focus",
                    style: TextStyle(
                      fontSize: 16,
                      fontWeight: FontWeight.bold,
                    ),
                  ),

                  SizedBox(height: 10),

                  /// Bullet points
                  Text("• UI Development"),
                  Text("• API Integration"),
                  Text("• State Management"),
                ],
              ),
            ),

            const SizedBox(height: 30),
          ],
        ),
      ),

      /// ================= FOOTER =================
      /// Floating button at bottom
      floatingActionButton: FloatingActionButton.extended(
        onPressed: () {},

        /// Button color
        backgroundColor: const Color(0xFFDDEBFF),

        label: const Text("Explore"),
        icon: const Icon(Icons.arrow_forward),
      ),
    );
  }
}

/// ================= STAT CARD =================
/// Reusable widget for showing small statistics
class _StatCard extends StatelessWidget {
  final String title;
  final String value;

  const _StatCard({
    required this.title,
    required this.value,
  });

  @override
  Widget build(BuildContext context) {
    return Container(
      width: 100,
      padding: const EdgeInsets.all(12),

      /// Styling for card
      decoration: BoxDecoration(
        color: const Color(0xFFF0F4FF),
        borderRadius: BorderRadius.circular(12),
      ),

      /// Column for value + label
      child: Column(
        children: [
          Text(
            value,
            style: const TextStyle(
              fontWeight: FontWeight.bold,
              fontSize: 16,
            ),
          ),
          const SizedBox(height: 4),
          Text(title, style: const TextStyle(fontSize: 12)),
        ],
      ),
    );
  }
}

/// ================= PROGRESS ROW =================
/// Reusable widget for progress bar
class _ProgressRow extends StatelessWidget {
  final String label;
  final double progress;

  const _ProgressRow({
    required this.label,
    required this.progress,
  });

  @override
  Widget build(BuildContext context) {
    return Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        /// Label text
        Text(label),

        const SizedBox(height: 4),

        /// Progress indicator (0.0 → 1.0)
        LinearProgressIndicator(
          value: progress,
          backgroundColor: Colors.grey.shade300,
          color: Colors.blue,
        ),
      ],
    );
  }
}
```

### 1. Structure

```
Scaffold  
 ├── AppBar (Header)  
 ├── Body (Scrollable UI)  
 └── Floating Button (Footer)
```
### 2. Layout Thinking

- Column → vertical layout
- Row → horizontal layout
- Container → styling
- SizedBox → spacing
### 3. Reusability

- `_StatCard`
- `_ProgressRow`

-- This is how real apps are built
### 4. Styling Basics

- `BoxDecoration` → colors + border radius
- `padding` → inner spacing
- `margin` → outer spacing (not used here but important)