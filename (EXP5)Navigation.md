# Side-Nav
1. main.dart : 
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: MyStatefulWidget(),
      theme: ThemeData(
        primaryColor: Colors.blue, // Customize primary color
      // Customize accent color
      ),
    );
  }
}

class MyStatefulWidget extends StatefulWidget {
  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  String _appBarTitle = 'Home';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(_appBarTitle),
      ),
      drawer: Drawer(
        elevation: 20.0,
        child: ListView(
          padding: EdgeInsets.zero,
          children: <Widget>[
            DrawerHeader(
              decoration: BoxDecoration(
                color: Theme.of(context).primaryColor,
              ),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  CircleAvatar(
                    backgroundColor: Colors.white,
                    child: Text("SIES", style: TextStyle(color: Theme.of(context).primaryColor)),
                  ),
                  SizedBox(height: 10),
                  Text(
                    "SIES GST",
                    style: TextStyle(color: Colors.white, fontSize: 18),
                  ),
                  Text(
                    "siesgst@gmail.com",
                    style: TextStyle(color: Colors.white),
                  ),
                ],
              ),
            ),
            ListTile(
              title: Text("Inbox"),
              leading: Icon(Icons.mail),
              onTap: () {
                Navigator.pop(context);
                setState(() {
                  _appBarTitle = 'Inbox';
                });
              },
            ),
            Divider(
              height: 0.1,
            ),
            ListTile(
              title: Text("Primary"),
              leading: Icon(Icons.inbox),
              onTap: () {
                Navigator.pop(context);
                setState(() {
                  _appBarTitle = 'Primary';
                });
              },
            ),
            ListTile(
              title: Text("Social"),
              leading: Icon(Icons.people),
              onTap: () {
                Navigator.pop(context);
                setState(() {
                  _appBarTitle = 'Social';
                });
              },
            ),
            ListTile(
              title: Text("Promotions"),
              leading: Icon(Icons.local_offer),
              onTap: () {
                Navigator.pop(context);
                setState(() {
                  _appBarTitle = 'Promotions';
                });
              },
            ),
          ],
        ),
      ),
      body: Center(
        child: Text(
          'Welcome to $_appBarTitle',
          style: TextStyle(fontSize: 20),
        ),
      ),
    );
  }
}

```
# Bottom-nav
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: MyStatefulWidget(),
      theme: ThemeData(
        primaryColor: Colors.blue, // Customize primary color
      ),
    );
  }
}

class MyStatefulWidget extends StatefulWidget {
  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  String _appBarTitle = 'MailScanner';
  int _selectedIndex = 0;

  static const List<Widget> _widgetOptions = <Widget>[
    Text('MailScanner Screen'),
    Text('Primary Screen'),
    Text('Social Screen'),
    Text('Promotions Screen'),
  ];

  void _onItemTapped(int index) {
    setState(() {
      _selectedIndex = index;
      switch (index) {
        case 0:
          _appBarTitle = 'MailScanner';
          break;
        case 1:
          _appBarTitle = 'Primary';
          break;
        case 2:
          _appBarTitle = 'Social';
          break;
        case 3:
          _appBarTitle = 'Promotions';
          break;
      }
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(_appBarTitle),
      ),
      body: Center(
        child: _widgetOptions.elementAt(_selectedIndex),
      ),
      bottomNavigationBar: BottomNavigationBar(
        backgroundColor: Colors.blue, // Background color of the navigation bar
        items: const <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            icon: Icon(Icons.mail),
            label: 'Inbox',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.inbox),
            label: 'Primary',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.people),
            label: 'Social',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.local_offer),
            label: 'Promotions',
          ),
        ],
        currentIndex: _selectedIndex,
        selectedItemColor: Color.fromARGB(255, 7, 134, 79), // Color of selected item
        unselectedItemColor:  Colors.blue, // Color of unselected items
        onTap: _onItemTapped,
      ),
    );
  }
}

```
