# Layout_widgets

1. create "assets" folder and add images in it
2. add the asset's details in pubspec.yaml : 
```dart
flutter:
  assets:
    - assets/img1.png
    - assets/img2.png
    - assets/img3.png
```
# column widget + row widget
3. main.dart code for <b>column widget<b> (For row replace child element name to "Row()") : 
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Layout Demo',
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Flutter Layout Demo'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            ChildWidget(
              imagePath: 'assets/img1.png',
              text: 'Flutter',
            ),
            SizedBox(height: 20),
            ChildWidget(
              imagePath: 'assets/img2.png',
              text: 'Dart',
            ),
            SizedBox(height: 20),
            ChildWidget(
              imagePath: 'assets/img3.png',
              text: 'Material',
            ),
          ],
        ),
      ),
    );
  }
}

class ChildWidget extends StatelessWidget {
  final String imagePath;
  final String text;

  const ChildWidget({
    Key? key,
    required this.imagePath,
    required this.text,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        CircleAvatar(
          radius: 50,
          backgroundImage: AssetImage(imagePath),
        ),
        SizedBox(height: 10),
        Text(
          text,
          style: TextStyle(fontSize: 18),
        ),
      ],
    );
  }
}
```
4. If error thrown : 
```bash
Error while trying to load an asset: Flutter Web engine failed to fetch "assets/assets/img3.png". HTTP request succeeded, but  
the server responded with HTTP status 404.
```
5. Run(in terminal) : 
```bash
flutter build web --web-renderer html --release
```
6. Re-run flutter run : 
```bash
flutter run
```
# List + grid view
7. List
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter ListView Demo',
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Flutter ListView Demo'),
      ),
      body: ListView(
        scrollDirection: Axis.vertical,
        children: <Widget>[
          ChildWidget(
            imagePath: 'assets/img1.png',
            text: 'Flutter',
          ),
          SizedBox(width: 20),
          ChildWidget(
            imagePath: 'assets/img2.png',
            text: 'Dart',
          ),
          SizedBox(width: 20),
          ChildWidget(
            imagePath: 'assets/img3.png',
            text: 'Material',
          ),
        ],
      ),
    );
  }
}

class ChildWidget extends StatelessWidget {
  final String imagePath;
  final String text;

  const ChildWidget({
    Key? key,
    required this.imagePath,
    required this.text,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Row(
      children: [
        CircleAvatar(
          radius: 50,
          backgroundImage: AssetImage(imagePath),
        ),
        SizedBox(width: 10),
        Text(
          text,
          style: TextStyle(fontSize: 18),
        ),
      ],
    );
  }
}
```
8. Grid view
```bash
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter GridView Demo',
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Flutter GridView Demo'),
      ),
      body: GridView.count(
        crossAxisCount: 2,
        children: <Widget>[
          ChildWidget(
            imagePath: 'assets/img1.png',
            text: 'Flutter',
          ),
          ChildWidget(
            imagePath: 'assets/img2.png',
            text: 'Dart',
          ),
          ChildWidget(
            imagePath: 'assets/img3.png',
            text: 'Material',
          ),
        ],
      ),
    );
  }
}

class ChildWidget extends StatelessWidget {
  final String imagePath;
  final String text;

  const ChildWidget({
    Key? key,
    required this.imagePath,
    required this.text,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        CircleAvatar(
          radius: 50,
          backgroundImage: AssetImage(imagePath),
        ),
        SizedBox(height: 10),
        Text(
          text,
          style: TextStyle(fontSize: 18),
        ),
      ],
    );
  }
}
```
