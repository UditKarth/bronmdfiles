# Flutter  Quick Start Guide
Flutter is Google's UI toolkit for crafting beautiful, natively compiled applications for mobile, web, and desktop from a single codebase. 

## Prerequisites
Ensure you have Flutter installed on your machine. Flutter requires the latest version of the Flutter SDK and Dart. Verify your Flutter installation by running:

```
flutter doctor
```
## Creating a New Flutter Project
To create a new Flutter project, run:
```
flutter create my_app
cd my_app
```

## Running Your App
To run your Flutter app, ensure an emulator is running or a device is connected to your computer. Then execute:
```
flutter run
```
This command compiles your app and launches it on the emulator or device.

## Understanding Flutter Widgets
Flutter apps are built using widgets, which are the basic building blocks of the app's UI. Each widget is an immutable declaration of part of the user interface.

### Stateful and Stateless Widgets
- Stateless Widgets: Widgets that don't store state. They are immutable, meaning their properties can't change—all values are final.
```
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Welcome to Flutter')),
        body: Center(child: Text('Hello, Hackathon!')),
      ),
    );
  }
}

```
- Stateful Widgets: Widgets that maintain state that might change during the lifetime of the widget. Implementing a stateful widget requires at least two classes: a StatefulWidget class that creates an instance of a State class.
```
class Counter extends StatefulWidget {
  @override
  _CounterState createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Counter')),
      body: Center(child: Text('You have pushed the button $_counter times.')),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ),
    );
  }
}

```

## Handling Events
Events in Flutter, such as user interactions, are handled by attaching event listeners to widgets. You can respond to gestures using the widgets in flutter:gestures.
```
GestureDetector(
  onTap: () {
    // Handle tap event
  },
  child: Container(
    padding: EdgeInsets.all(12.0),
    decoration: BoxDecoration(
      color: Theme.of(context).buttonColor,
      borderRadius: BorderRadius.circular(8.0),
    ),
    child: Text('My Button'),
  ),
)

```
## Conditional Rendering
Flutter allows you to build your UI dynamically based on state and other conditions. Use Dart's control flow features within your widget build methods to conditionally include widgets in the tree.
```
Widget build(BuildContext context) {
  return _isLoggedIn ? HomePage() : LoginPage();
}
```
## State Management
State management is crucial in Flutter to manage the state of your app efficiently. There are various approaches to state management in Flutter, from simple local state management using setState, to more complex solutions like Provider, Riverpod, Bloc, and Redux.

- Provider: A wrapper around InheritedWidget to make it easier to use and more reusable.
```
ChangeNotifierProvider(
  create: (context) => MyModel(),
  child: MyApp(),
);

```
- Bloc/Cubit: Stands for Business Logic Component, separates the presentation layer from business logic, making your code more testable and reusable.

## Building and Shipping
To build a release version of your Flutter app:

For Android:
```
flutter build apk
```
For iOS:
```
flutter build ios
```

## Additional Tips
Widgets Catalog: Explore Flutter's widget catalog to familiarize yourself with the available UI components.
Pub Packages: Utilize pub.dev to find reusable packages published by the Flutter community to speed up development.
Hot Reload: Use Flutter's Hot Reload feature to see the effects of your changes in real-time without restarting your app.