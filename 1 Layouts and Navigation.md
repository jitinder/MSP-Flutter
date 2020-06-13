## Talk 1: Layouts and Navigation

The following code is based on the code from [Flutter.dev docs](https://flutter.dev/docs/get-started/codelab#step-1-create-the-starter-flutter-app). It creates a Hello World Stateless Screen that we will use as a base to write our code in.


    import 'package:flutter/material.dart';
    
    void main() {
      runApp(MaterialApp(
        title: 'Sidak\'s Portfolio',
        debugShowCheckedModeBanner: false,
        theme: ThemeData(
          primaryColor: Colors.orange[800],
          accentColor: Colors.orangeAccent,
        ),
        home: MyApp(),
      ));
    }
    
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Sidak\'s Portfolio'),
          ),
          body: Center(
            child: Text('Hello World'),
          ),
        );
      }
    }

<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>Intentional<br/><br/>Line<br/><br/>Breaks<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

## The Final Code

This code is given as a reference for those who are absolutely stuck and have no idea about what to do. **DO NOT** copy-paste this code in the very beginning as that defeats 

    import 'package:flutter/material.dart';
    
    void main() {
      runApp(MaterialApp(
        title: 'Sidak\'s Portfolio',
        debugShowCheckedModeBanner: false,
        theme: ThemeData(
          primaryColor: Colors.orange[800],
          accentColor: Colors.orangeAccent,
        ),
    //     home: MyApp(),
        initialRoute: '/',
        routes: {
          '/': (context) => MyApp(),
          '/info': (context) => MyInfo(),
        },
      ));
    }
    
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Sidak\'s Portfolio'),
          ),
          body: Column(
            children: [
              Padding(
                padding: const EdgeInsets.all(16.0),
                child: Column(
                  children: [
                    Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          Column(
                            crossAxisAlignment: CrossAxisAlignment.start,
                            children: [
                              Text("Sidak Pasricha",
                                  style: TextStyle(fontWeight: FontWeight.bold)),
                              Text("3rd year Computer Science, UCL",
                                  style: TextStyle(color: Colors.grey[500])),
                            ],
                          ),
                          IconButton(
                            onPressed: () {
    //                             Navigator.push(
    //                               context,
    //                               MaterialPageRoute(builder: (context) => MyInfo()),
    //                             );
                              Navigator.pushNamed(context, "/info");
                            },
                            icon: Icon(Icons.info),
                            tooltip: "Info",
                          ),
                        ]),
                    Container(
                      margin: EdgeInsets.only(top: 16),
                      alignment: Alignment.centerLeft,
                      child: Text("Language Proficiency:",
                          style: TextStyle(fontWeight: FontWeight.bold)),
                    ),
                    Container(
                      margin: EdgeInsets.only(top: 8),
                      child: Row(
                          mainAxisAlignment: MainAxisAlignment.spaceBetween,
                          children: [
                            Text("Java"),
                            makeStars(4),
                          ]),
                    ),
                    Container(
                      margin: EdgeInsets.only(top: 8),
                      child: Row(
                          mainAxisAlignment: MainAxisAlignment.spaceBetween,
                          children: [
                            Text("Python"),
                            makeStars(3),
                          ]),
                    ),
                  ],
                ),
              ),
            ],
          ),
        );
      }
    
      Widget makeStars(int n) {
        List<Widget> stars = new List();
        if (n < 0) {
          n = 0;
        }
        if (n > 5) {
          n = 5;
        }
        Color color = Colors.red;
        switch (n) {
          case 1:
            color = Colors.red[400];
            break;
          case 2:
            color = Colors.deepOrange;
            break;
          case 3:
            color = Colors.amber;
            break;
          case 4:
            color = Colors.green[400];
            break;
          case 5:
            color = Colors.green[700];
            break;
          default:
            color = Colors.red;
        }
        for (int i = 0; i < n; i++) {
          stars.add(Icon(Icons.star, color: color));
        }
        for (int i = 5 - n; i > 0; i--) {
          stars.add(Icon(Icons.star_border, color: color));
        }
        return Row(children: stars);
      }
    }
    
    class MyInfo extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text("Sidak's Info"),
          ),
          body: Container(
            alignment: Alignment.center,
            padding: EdgeInsets.all(16),
            child: Text(
              "I don't know enough 'Lorem ipsum dolor sit amet' to fill this page up, and I'd rather not talk about my bare minimum achievements, hopefully you guys can fill this up with some actually interesting stuff... Peace",
              textAlign: TextAlign.justify,
            ),
          ),
        );
      }
    }

