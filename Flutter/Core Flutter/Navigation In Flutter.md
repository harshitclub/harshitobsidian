Flutter uses a tool called the `Navigator` to manage this deck of cards. Here is the simplest, most detailed guide to mastering basic navigation.

### **1. Going Forward: `Navigator.push()`**

When you want to move from Screen A to Screen B, you "push" Screen B onto the stack.

Here is the exact code you use inside an `onPressed` or `onTap` event:

```
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => const ScreenB()),
);
```

**What is happening here?**

- **`Navigator.push`**: This is the command telling Flutter to add a new screen to the top of the pile.
- **`context`**: This is your current widget's GPS location. The Navigator needs to know exactly where you are right now before it can move you somewhere else.
- **`MaterialPageRoute`**: Flutter doesn't just instantly snap to the next screen. `MaterialPageRoute` is a wrapper that handles the smooth transition animation (like sliding in from the right on iOS, or fading up from the bottom on Android).
- **`builder: (context) => const ScreenB()`**: This is simply you telling Flutter exactly which screen to build and show.
### **2. Going Backward: `Navigator.pop()`**

When you are on Screen B and want to go back to Screen A, you "pop" Screen B off the top of the stack.

_Note: The built-in back button in the `AppBar` and your phone's physical back button do this automatically! You only need to write this code if you are making a custom back button, like a "Cancel" or "Submit" button in the middle of the screen._

```
Navigator.pop(context);
```

**What is happening here?**

- **`Navigator.pop`**: Tells Flutter, _"Destroy the screen I am currently looking at and show me whatever was underneath it."_
- **`context`**: Again, it just needs to know where you are so it knows which screen to destroy.
### **3. The Complete Practical Example**

Here is a bare-minimum, copy-pasteable example of two screens talking to each other. Notice how simple the logic is.

```
import 'package:flutter/material.dart';

void main() {
  runApp(const MaterialApp(
    home: FirstScreen(), // The app starts here
  ));
}

// --- SCREEN 1 ---
class FirstScreen extends StatelessWidget {
  const FirstScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('First Screen')),
      body: Center(
        child: ElevatedButton(
          child: const Text('Go to Second Screen'),
          onPressed: () {
            // THE NAVIGATION CODE
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => const SecondScreen()),
            );
          },
        ),
      ),
    );
  }
}

// --- SCREEN 2 ---
class SecondScreen extends StatelessWidget {
  const SecondScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Second Screen')),
      body: Center(
        child: ElevatedButton(
          style: ElevatedButton.styleFrom(backgroundColor: Colors.red),
          child: const Text('Go Back', style: TextStyle(color: Colors.white)),
          onPressed: () {
            // THE GO BACK CODE
            Navigator.pop(context);
          },
        ),
      ),
    );
  }
}
```
### **A Quick Note on Passing Data**

If you want to send information from the First Screen to the Second Screen (like clicking a user's name to see their profile), you don't need any special navigation code. You just pass it directly into the Second Screen's constructor, exactly like we did in the Zenith and Oasis apps!

```
// Pushing the screen and passing a string into it
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const ProfileScreen(userName: 'Alex'),
  ),
);
```

This method (`push` and `pop`) is perfect for 80% of apps.