### **The 3 Core Steps**

1. **Create the Controller:** `final myController = TextEditingController();`
2. **Attach it:** `TextField(controller: myController)`
3. **Read it:** `myController.text`
### **The Bare Minimum Example

This app just has one text box, one button, and one text output. No complex design, just pure logic.

```
import 'package:flutter/material.dart';

void main() {
  runApp(const MaterialApp(
    debugShowCheckedModeBanner: false,
    home: SimpleInputApp(),
  ));
}

class SimpleInputApp extends StatefulWidget {
  const SimpleInputApp({super.key});

  @override
  State<SimpleInputApp> createState() => _SimpleInputAppState();
}

class _SimpleInputAppState extends State<SimpleInputApp> {
  // STEP 1: Create the controller (The "Microphone")
  final TextEditingController _nameController = TextEditingController();

  // A variable to hold the text after we click the button
  String _messageToDisplay = "Type your name and hit submit!";

  // STEP 2: The function that runs when the button is clicked
  void _grabData() {
    setState(() {
      // Read whatever is inside the controller right now
      String grabbedText = _nameController.text;
      
      // Update our screen message
      _messageToDisplay = "Hello, $grabbedText!"; 
    });
  }

  // Always throw away controllers when the screen closes to save RAM
  @override
  void dispose() {
    _nameController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Simple Input')),
      body: Padding(
        padding: const EdgeInsets.all(50.0), // Adds space around the edges
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            // STEP 3: Attach the controller to the text box
            TextField(
              controller: _nameController, 
              decoration: const InputDecoration(
                border: OutlineInputBorder(), // Adds a simple box outline
                hintText: 'Enter your name here...',
              ),
            ),
            
            const SizedBox(height: 20), // Spacing
            
            // THE SUBMIT BUTTON
            ElevatedButton(
              onPressed: _grabData, // Trigger the function when clicked
              child: const Text('SUBMIT'),
            ),
            
            const SizedBox(height: 40), // Spacing
            
            // THE OUTPUT TEXT
            Text(
              _messageToDisplay,
              style: const TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
            ),
          ],
        ),
      ),
    );
  }
}
```

### **How it flows:**

1. You type "Alex" into the `TextField`. The `_nameController` quietly holds onto the word "Alex" in the background.
2. You click the "SUBMIT" button.
3. The button fires the `_grabData` function.
4. The function asks `_nameController.text` what it is holding. It gets "Alex".
5. `setState` redraws the screen, updating the text at the bottom to say "Hello, Alex!".

This is the cleanest, most fundamental way to handle inputs in Flutter.