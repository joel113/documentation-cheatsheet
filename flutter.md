# Flutter

https://flutter.dev

https://api.flutter.dev/index.html

https://docs.flutter.dev/cookbook

## Widgets

https://docs.flutter.dev/development/ui/widgets-intro

### Scaffold

https://api.flutter.dev/flutter/material/Scaffold-class.html

### ListTile

https://api.flutter.dev/flutter/material/ListTile-class.html

### ListView

### ListView.Builder

For some tasks it is best to swtich from the ListView to the ListView.Builder. The default ListView builder requires all items at once.

https://medium.com/@AnInsightfulTechie/flutter-displaying-dynamic-contents-using-listview-builder-f2cedb1a19fb

### Container

https://api.flutter.dev/flutter/widgets/Container-class.html

### Padding

https://api.flutter.dev/flutter/widgets/Padding-class.html

### EdgeInsets

https://api.flutter.dev/flutter/painting/EdgeInsets-class.html

## Component Lifecycle

https://medium.flutterdevs.com/explore-widget-lifecycle-in-flutter-e36031c697d0

## Flutter using Dart

https://dart.dev/

https://dart.dev/codelabs/dart-cheatsheet

https://dartpad.dev/?

### Classes

#### Optional Parameters

https://stackoverflow.com/questions/52449508/constructor-optional-params

### Enumerations

https://stackoverflow.com/questions/38908285/how-do-i-add-methods-or-values-to-enums-in-dart

### Null Safety

https://dart.dev/null-safety

https://dart.dev/null-safety/understanding-null-safety

#### Exclamation Mark

The exclamation mark `!` is used in dart to cast from a nullable to a non-nullable type. It should be only used if it is guaranteed that the value will never hold a null value. It should be not confused with a conditional access to a property.

https://stackoverflow.com/questions/63253015/what-does-the-exclamation-mark-mean-before-a-function-call

#### Conditional Property Access

https://dart.dev/codelabs/dart-cheatsheet#conditional-property-access

### DateTime

https://api.flutter.dev/flutter/dart-core/DateTime-class.html

https://pub.dev/documentation/intl/latest/intl/DateFormat-class.html

#### Format DateTime with DateFormat

https://stackoverflow.com/questions/54371874/how-get-the-name-of-the-days-of-the-week-in-dart

### Futures

https://dart.dev/codelabs/async-await

https://dart.dev/guides/libraries/futures-error-handling

https://stackoverflow.com/questions/46579358/getting-values-from-future-instances

https://stackoverflow.com/questions/59927528/how-to-refresh-listview-builder-flutter

### State

The `setState()` opration notifies the flutter framework that the application state has been changed and that the user interface might have to be redrawn. The framework might redraw some components in the ui tree, which causes a call to the build method of the components.

https://api.flutter.dev/flutter/widgets/State/setState.html

### Restoration Mixin

State resotration is a system that allows your app to save and restore its state when the user bakcgrounds and then resumes the app, or when the app is terminated and then restarted by the system.

RestorationMixin is a crucial component of Flutter's state restoration strategy for stateful widgets. It provides the base functionality that allows you to:

1. Register Restorable Properties: You use RestorationMixin to register properties that should be saved and restored during state restoration (e.g., text values from TextField widgets, currently selected tab, data values from business logic).

2. Restore State: When the app is resumed, RestorationMixin restores the values of the registered properties automatically.

3. Manage Restorable Values: The RestorationMixin has methods to properly dispose and manage values during the lifetime of the widget.

4. Work with the Restoration System: RestorationMixin integrates with the framework's restoration system and provides the right calls at the right moment during state restoration.

#### Key Concepts

* RestorableProperty: A base class for restorable properties. You use concrete implementations of this to store state. The framework knows how to save the properties and restore them to a value. The available properties are
    * RestorableBool
    * RestorableDouble
    * RestorableInt
    * RestorableString
    * RestorableTextEditingController
    * RestorableValue<T>: Use this for complex objects, you need to implement the toPrimitives and the fromPrimitives method of the class you want to restore.
* restoreState Function: A callback called during state restoration, to allow you to perform actions after the restorable values are loaded.
* registerForRestoration Method: Method that registers a RestorableProperty. You must register properties in the initState of your widget.
* Automatic Restoration IDs: The framework automatically assigns restoration IDs to widgets that use RestorationMixin. These IDs are used to uniquely identify each state.

### Reading and Writing Files

https://docs.flutter.dev/cookbook/persistence/reading-writing-files

#### Directories

https://api.dart.dev/stable/2.18.0/dart-io/Directory-class.html

https://stackoverflow.com/questions/14268967/how-do-i-list-the-contents-of-a-directory-with-dart

#### Assets and Images

https://docs.flutter.dev/development/ui/assets-and-images#sharing-assets-with-the-underlying-platform
	
#### JSON Serialization and Deserialization

https://docs.flutter.dev/development/data-and-backend/json

## Lambda and Arrow Functions vs. Anonymous Functions

https://stackoverflow.com/questions/59379354/how-to-call-multi-statements-when-flutter-is-started-with

### Cocoapods

https://stackoverflow.com/questions/64901180/how-to-run-cocoapods-on-apple-silicon-m1
