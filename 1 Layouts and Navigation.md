## Talk 1: Layouts and Navigation

The following code was taken from the [Flutter.dev docs](https://flutter.dev/docs/get-started/codelab#step-1-create-the-starter-flutter-app). It creates a Hello World Stateless Screen that we will use as a base to write our code in.


    import 'package:flutter/material.dart';
    
    void main() => runApp(MyApp());
    
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Welcome to Flutter',
          home: Scaffold(
            appBar: AppBar(
              title: Text('Welcome to Flutter'),
            ),
            body: Center(
              child: Text('Hello World'),
            ),
          ),
        );
      }
    }

