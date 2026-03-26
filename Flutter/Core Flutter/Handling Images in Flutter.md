### **1. The Quick Way: Network Images**

Grab an image straight from a URL. No setup required.

```
Image.network(
  'https://your-image-url.com/pic.jpg',
)
```
### **2. The Local Way: Asset Images**

For things like logos that need to be bundled inside the app so they load instantly without the internet.

**Step A: Create the folder** Create a folder named `assets` in your main project directory, and drop your image (e.g., `logo.png`) inside it.

**Step B: Register it in `pubspec.yaml`** Open `pubspec.yaml` and add the assets section under `flutter:`. _(Watch the spaces! YAML is strict about indentation)._

```
flutter:
  uses-material-design: true
  assets:
    - assets/logo.png
```

**Step C: Show it in your code**

```
Image.asset(
  'assets/logo.png',
)
```

### **3. Basic Image Styling**

Images usually need to be resized, cropped, or have their corners rounded. Here is how you do the three most common styles.
#### **A. Resizing and Cropping (The CSS `object-fit` equivalent)**

Wrap the image in a specific `width` and `height`, and use the `fit` property so it doesn't look stretched or squished.

```
Image.network(
  'https://your-image-url.com/pic.jpg',
  width: 200,
  height: 200,
  fit: BoxFit.cover, // Crops the edges so it completely fills the 200x200 box
)
```

#### **B. Rounded Corners (The CSS `border-radius` equivalent)**

To round the edges of an image, you wrap it inside a `ClipRRect` (Clip Rounded Rectangle) widget.

```
ClipRRect(
  borderRadius: BorderRadius.circular(15.0), 
  child: Image.asset(
    'assets/logo.png',
    width: 150,
    height: 150,
    fit: BoxFit.cover,
  ),
)
```

#### **C. Perfect Circles (For Profile Pictures)**

Don't try to manually calculate the border radius to make a circle. Flutter has a built-in widget specifically for this.

```
const CircleAvatar(
  radius: 60, // The size of the circle
  backgroundImage: NetworkImage('https://your-image-url.com/profile.jpg'),
)
```

_(Notice it uses `NetworkImage` instead of `Image.network` here—that's because `CircleAvatar` specifically asks for an image provider, not an image widget)._