# Responsive_UI
1. Device Preview (Replace the original void main with the below one also update pubspec.yaml):
```dart
//Import in main.dart
import 'package:device_preview/device_preview.dart'; 
```
```dart
dev_dependencies:
  flutter_test:
    sdk: flutter
  flutter_lints: ^2.0.0
  device_preview: ^0.7.5
```
```dart
void main() {
  runApp(
    DevicePreview(
      builder: (context) => MyApp(),
    ),
  );
}
```
2. Using layoutBuilder Class :
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Responsive Flutter App',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Responsive Flutter App'),
      ),
      body: Center(
        child: LayoutBuilder(
          builder: (context, constraints) {
            if (constraints.maxWidth < 600) {
              // Mobile layout
              return Column(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  _buildBlock(Colors.green, 'Block 1'),
                  SizedBox(height: 20),
                  _buildBlock(Colors.orange, 'Block 2'),
                ],
              );
            } else {
              // Tablet/Desktop layout
              return Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Expanded(
                    flex: 1,
                    child: _buildBlock(Colors.green, 'Block 1'),
                  ),
                  SizedBox(width: 20),
                  Expanded(
                    flex: 1,
                    child: _buildBlock(Colors.orange, 'Block 2'),
                  ),
                ],
              );
            }
          },
        ),
      ),
    );
  }

  Widget _buildBlock(Color color, String text) {
    return Container(
      width: 150,
      height: 150,
      color: color,
      child: Center(
        child: Text(
          text,
          style: TextStyle(fontSize: 20, color: Colors.white),
        ),
      ),
    );
  }
}
```
3. Using MediaQuery :
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Responsive Flutter App',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final mediaQuery = MediaQuery.of(context);
    final isMobile = mediaQuery.size.width < 600;

    return Scaffold(
      appBar: AppBar(
        title: Text('Responsive Flutter App'),
      ),
      body: Center(
        child: isMobile ? _buildMobileLayout() : _buildTabletDesktopLayout(),
      ),
    );
  }

  Widget _buildMobileLayout() {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        _buildBlock(Colors.green, 'Block 1'),
        SizedBox(height: 20),
        _buildBlock(Colors.orange, 'Block 2'),
      ],
    );
  }

  Widget _buildTabletDesktopLayout() {
    return Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        Expanded(
          flex: 1,
          child: _buildBlock(Colors.green, 'Block 1'),
        ),
        SizedBox(width: 20),
        Expanded(
          flex: 1,
          child: _buildBlock(Colors.orange, 'Block 2'),
        ),
      ],
    );
  }

  Widget _buildBlock(Color color, String text) {
    return Container(
      width: 150,
      height: 150,
      color: color,
      child: Center(
        child: Text(
          text,
          style: TextStyle(fontSize: 20, color: Colors.white),
        ),
      ),
    );
  }
}

```
