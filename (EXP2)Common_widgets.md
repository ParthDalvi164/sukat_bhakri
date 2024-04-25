# Common_widgets

1. Code for main.dart : 
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter UI Demo',
      home: MyHomePage(),
      debugShowCheckedModeBanner: false,
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Flutter UI Demo'), // AppBar Widget
        backgroundColor: Colors.blue, // Customizing AppBar color
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'Hello, Flutter!', // Text Widget
              style: TextStyle(fontSize: 24),
            ),
            SizedBox(height: 20), // Adding spacing between widgets
            ElevatedButton(
              onPressed: () {
                // Button Pressed
              },
              child: Text('Click Me'), // ElevatedButton Widget
            ),
            SizedBox(height: 20), // Adding spacing between widgets
            Container(
              width: 200,
              height: 200,
              color: Colors.blue, // Container Widget
              child: Center(
                child: Text(
                  'Container', // Text Widget inside Container
                  style: TextStyle(color: Colors.white, fontSize: 20),
                ),
              ),
            ),
            SizedBox(height: 20), // Adding spacing between widgets
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: <Widget>[
                Text('Row 1:'), // Text Widget inside Row
                Text(' City '), // Text Widget inside Row
                Text(' United '), // Text Widget inside Row
              ],
            ),
          ],
        ),
      ),
    );
  }
}

```
2. Excution : 
```bash
flutter run
```
