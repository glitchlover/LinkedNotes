#Note-Flutter #Done

# Write your first Flutter app, part 1

1. [Docs](https://flutter.dev/docs) 
2. [Get started](https://flutter.dev/docs/get-started) 
3. [Write your first app](https://flutter.dev/docs/get-started/codelab.html) 

Contents

- [Step 1: Create the starter Flutter app](https://flutter.dev/docs/get-started/codelab#step-1-create-the-starter-flutter-app)
- [Step 2: Use an external package](https://flutter.dev/docs/get-started/codelab#step-2-use-an-external-package)
- [Step 3: Add a Stateful widget](https://flutter.dev/docs/get-started/codelab#step-3-add-a-stateful-widget)
- [Step 4: Create an infinite scrolling ListView](https://flutter.dev/docs/get-started/codelab#step-4-create-an-infinite-scrolling-listview)
- [Profile or release runs](https://flutter.dev/docs/get-started/codelab#profile-or-release-runs)

**Tip:** This codelab walks you through writing your first Flutter app on mobile. You might prefer to try [writing your first Flutter app on the web](https://flutter.dev/docs/get-started/codelab-web). **Note that if you have [enabled web](https://flutter.dev/docs/get-started/web), the completed app just works on all of these devices!**

![https://flutter.dev/assets/get-started/android/hello-world-fadb9765c01d33f0fea92d7ac767e036ea90e9159335ea1841277bc6bef3a10a.png](https://flutter.dev/assets/get-started/android/hello-world-fadb9765c01d33f0fea92d7ac767e036ea90e9159335ea1841277bc6bef3a10a.png)

This is a guide to creating your first Flutter app. If you are familiar with object-oriented code and basic programming concepts such as variables, loops, and conditionals, you can complete this tutorial. You don’t need previous experience with Dart, mobile, or web programming.

This codelab is part 1 of a two-part codelab. You can find [part 2](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2) on [Google Developers Codelabs](https://codelabs.developers.google.com/) (as well as a copy of this codelab, [part 1](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt1)).

## What you’ll build in part 1

You’ll implement a simple app that generates proposed names for a startup company. The user can select and unselect names, saving the best ones. The code lazily generates 10 names at a time. As the user scrolls, more names are generated. There is no limit to how far a user can scroll.

The animated GIF shows how the app works at the completion of part 1.

#### What you’ll learn in part 1

- How to write a Flutter app that looks natural on iOS, Android, and the web
- Basic structure of a Flutter app
- Finding and using packages to extend functionality
- Using hot reload for a quicker development cycle
- How to implement a stateful widget
- How to create an infinite, lazily loaded list

In [part 2](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2) of this codelab, you’ll add interactivity, modify the app’s theme, and add the ability to navigate to a new screen (called a _route_ in Flutter).

#### What you'll use

You need two pieces of software to complete this lab: the [Flutter SDK](https://flutter.dev/docs/get-started/install) and [an editor](https://flutter.dev/docs/get-started/editor). This codelab assumes Android Studio, but you can use your preferred editor.

You can run this codelab by using any of the following devices:

- A physical device ([Android](https://flutter.dev/docs/get-started/install/macos#set-up-your-android-device) or [iOS](https://flutter.dev/docs/get-started/install/macos#deploy-to-ios-devices)) connected to your computer and set to developer mode
- The [iOS simulator](https://flutter.dev/docs/get-started/install/macos#set-up-the-ios-simulator) (requires installing Xcode tools)
- The [Android emulator](https://flutter.dev/docs/get-started/install/macos#set-up-the-android-emulator) (requires setup in Android Studio)
- A browser (Chrome is required for debugging)

If you want to compile your app to run on the web, you must enable this feature (which is currently in beta). To enable web support, use the following instructions:



```
$ flutter channel beta
$ flutter upgrade
$ flutter config --enable-web
```

You need only run the config command once. After you enable web support, every Flutter app you create also compiles for the web. In your IDE under the **devices** pulldown, or at the command line using `flutter devices`, you should now see **Chrome** and **Web server** listed. The **Chrome** device automatically starts Chrome. The **Web server** starts a server that hosts the app so that you can load it from any browser. Use the Chrome device during development so that you can use DevTools, and the web server when you want to test on other browsers. For more information, see [Building a web application with Flutter](https://flutter.dev/web) and [Write your first Flutter app on the web](https://flutter.dev/docs/get-started/codelab-web).

## Step 1: Create the starter Flutter app

Create a simple, templated Flutter app, using the instructions in [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive#create-app). Name the project **startup\_namer** (instead of _flutter\_app_).

**Tip:** If you don’t see “New Flutter Project” as an option in your IDE, make sure you have the [plugins installed for Flutter and Dart](https://flutter.dev/docs/get-started/editor).

You’ll mostly edit **lib/main.dart**, where the Dart code lives.

1. Replace the contents of `lib/main.dart`.  
    Delete all of the code from **lib/main.dart**. Replace with the following code, which displays “Hello World” in the center of the screen.
    
    lib/main.dart
    
    
    
   ```dart
   // Copyright 2018 The Flutter team. All rights reserved. // Use of this source code is governed by a BSD-style license that can be // found in the LICENSE file. import 'package:flutter/material.dart'; 
   void main() \=> runApp(MyApp()); 
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
   ```
    
    **Tip:** When pasting code into your app, indentation can become skewed. You can fix this with the following Flutter tools:
    
    - Android Studio and IntelliJ IDEA: Right-click the code and select **Reformat Code with dartfmt**.
    - VS Code: Right-click and select **Format Document**.
    - Terminal: Run `flutter format <filename>`.
    
2. Run the app [in the way your IDE describes](https://flutter.dev/docs/get-started/test-drive). You should see either Android, iOS, or web output, depending on your device.
    
    ![Hello world app on Android](https://flutter.dev//get-started/android/hello-world-fadb9765c01d33f0fea92d7ac767e036ea90e9159335ea1841277bc6bef3a10a.png)
    
    Android
    
    ![Hello world app on iOS](https://flutter.dev//get-started/ios/hello-world-ed7cf47213953bfca5eaa74fba63a78538d782f2c63a7c575068f3c2f7298bde.png)
    
    iOS
    
    **Tip:** The first time you run on a physical device, it can take awhile to load. Afterward, you can use hot reload for quick updates. **Save** also performs a hot reload if the app is running. When running an app directly from the console using `flutter run`, enter `r` to perform hot reload.
    

### Observations

- This example creates a Material app. [Material Library](Material%20Library.md) is a visual design language that is standard on mobile and the web. Flutter offers a rich set of Material widgets. It’s a good idea to have a `uses-material-design: true` entry in the `flutter` section of your `pubspec.yaml` file. This will allow you to use more features of Material, such as their set of predefined [Icons](https://design.google.com/icons/).
    
- The `main()` method uses arrow (`=>`) notation. Use arrow notation for one-line functions or methods.
- The app extends `StatelessWidget`, which makes the app itself a widget. In Flutter, almost everything is a widget, including alignment, padding, and layout.
- The `Scaffold` widget, from the Material library, provides a default app bar, title, and a body property that holds the widget tree for the home screen. The widget subtree can be quite complex.
- A widget’s main job is to provide a `build()` method that describes how to display the widget in terms of other, lower level widgets.
- The body for this example consists of a `Center` widget containing a `Text` child widget. The Center widget aligns its widget subtree to the center of the screen.

## [](https://flutter.dev/docs/get-started/codelab#step-2-use-an-external-package)Step 2: Use an external package

In this step, you’ll start using an open-source package named [english\_words](https://pub.dev/packages/english_words), which contains a few thousand of the most used English words plus some utility functions.

You can find the `english_words` package, as well as many other open source packages, on [pub.dev](https://pub.dev/).

1. The `pubspec.yaml` file manages the assets and dependencies for a Flutter app. In `pubspec.yaml`, add `english_words` (3.1.5 or higher) to the dependencies list:
    
    {step1\_base → step2\_use\_package}/pubspec.yaml
    
    <table class="d2h-diff-table"><tbody class="d2h-diff-tbody"><tr><td class="d2h-code-linenumber d2h-info"></td><td class="d2h-info"><div class="d2h-code-line d2h-info">@@ -5,4 +5,5 @@</div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">5</div><div class="line-num2">5</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs yaml"><span class="hljs-attr">dependencies:</span></span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">6</div><div class="line-num2">6</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs yaml"><span class="hljs-attr">flutter:</span></span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">7</div><div class="line-num2">7</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs yaml"><span class="hljs-attr">sdk:</span> <span class="hljs-string">flutter</span></span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">8</div><div class="line-num2">8</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs yaml"><span class="hljs-attr">cupertino_icons:</span> <span class="hljs-string">^0.1.2</span></span></div></td></tr><tr><td class="d2h-code-linenumber d2h-ins"><div class="line-num1"></div><div class="line-num2">9</div></td><td class="d2h-ins"><div class="d2h-code-line d2h-ins"><span class="d2h-code-line-prefix">+</span> <span class="d2h-code-line-ctn hljs yaml"><span class="hljs-attr">english_words:</span> <span class="hljs-string">^3.1.5</span></span></div></td></tr></tbody></table>
    
2. While viewing the `pubspec.yaml` file in Android Studio’s editor view, click **Pub get**. This pulls the package into your project. You should see the following in the console:
    
    
    
    ```
    $ flutter pub get
    Running "flutter pub get" in startup_namer...
    Process finished with exit code 0
    ```
    
    Performing `Pub get` also auto-generates the `pubspec.lock` file with a list of all packages pulled into the project and their version numbers.
    
3. In `lib/main.dart`, import the new package:
    
    lib/main.dart
    
    
    
    import 'package:flutter/material.dart'; import 'package:english\_words/english\_words.dart';
    
    As you type, Android Studio gives you suggestions for libraries to import. It then renders the import string in gray, letting you know that the imported library is unused (so far).
    
4. Use the English words package to generate the text instead of using the string “Hello World”:
    
    {step1\_base → step2\_use\_package}/lib/main.dart
    
    <table class="d2h-diff-table"><tbody class="d2h-diff-tbody"><tr><td class="d2h-code-linenumber d2h-info"></td><td class="d2h-info"><div class="d2h-code-line d2h-info">@@ -9,6 +10,7 @@</div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">9</div><div class="line-num2">10</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MyApp</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatelessWidget</span> </span>{</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">10</div><div class="line-num2">11</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-meta">@override</span></span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">11</div><div class="line-num2">12</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">Widget build(BuildContext context) {</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-ins"><div class="line-num1"></div><div class="line-num2">13</div></td><td class="d2h-ins"><div class="d2h-code-line d2h-ins"><span class="d2h-code-line-prefix">+</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-keyword">final</span> wordPair = WordPair.random();</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">12</div><div class="line-num2">14</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-keyword">return</span> MaterialApp(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">13</div><div class="line-num2">15</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">title: <span class="hljs-string">'Welcome to Flutter'</span>,</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">14</div><div class="line-num2">16</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">home: Scaffold(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-info"></td><td class="d2h-info"><div class="d2h-code-line d2h-info">@@ -16,7 +18,7 @@</div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">16</div><div class="line-num2">18</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">title: Text(<span class="hljs-string">'Welcome to Flutter'</span>),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">17</div><div class="line-num2">19</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">18</div><div class="line-num2">20</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">body: Center(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">19</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">child: Text(<del><span class="hljs-string">'Hello World'</span></del>),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-ins"><div class="line-num1"></div><div class="line-num2">21</div></td><td class="d2h-ins"><div class="d2h-code-line d2h-ins"><span class="d2h-code-line-prefix">+</span> <span class="d2h-code-line-ctn hljs dart">child: Text(<ins>wordPair.asPascalCase</ins>),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">20</div><div class="line-num2">22</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">21</div><div class="line-num2">23</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">22</div><div class="line-num2">24</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">);</span></div></td></tr></tbody></table>
    
    **Note:** “Pascal case” (also known as “upper camel case”), means that each word in the string, including the first one, begins with an uppercase letter. So, “uppercamelcase” becomes “UpperCamelCase”.
    
5. If the app is running, [hot reload](https://flutter.dev/docs/get-started/test-drive) to update the running app. Each time you click hot reload, or save the project, you should see a different word pair, chosen at random, in the running app. This is because the word pairing is generated inside the build method, which is run each time the `MaterialApp` requires rendering, or when toggling the Platform in Flutter Inspector.
    
    ![App at completion of second step on Android](https://flutter.dev//get-started/android/step2-45e5a16e59926599e09b25b1c6d37372f77b69151cbebd070d2f94f657b1abde.png)
    
    Android
    
    ![App at completion of second step on iOS](https://flutter.dev//get-started/ios/step2-de9da90d2a90351c8d651c50f345c822472dbcd93cd8bad099e4edf2aa499c43.png)
    
    iOS
    

### Problems?

If your app is not running correctly, look for typos. If you want to try some of Flutter’s debugging tools, check out the [DevTools](https://flutter.dev/docs/development/tools/devtools) suite of debugging and profiling tools. If needed, use the code at the following links to get back on track.

- [pubspec.yaml](https://raw.githubusercontent.com/flutter/codelabs/master/startup_namer/step2_use_package/pubspec.yaml)
- [lib/main.dart](https://raw.githubusercontent.com/flutter/codelabs/master/startup_namer/step2_use_package/lib/main.dart)

## [](https://flutter.dev/docs/get-started/codelab#step-3-add-a-stateful-widget)Step 3: Add a Stateful widget

State_less_ widgets are immutable, meaning that their properties can’t change—all values are final.

State_ful_ widgets maintain state that might change during the lifetime of the widget. Implementing a stateful widget requires at least two classes: 1) a `StatefulWidget` class that creates an instance of 2) a `State` class. The `StatefulWidget` class is, itself, immutable and can be thrown away and regenerated, but the `State` class persists over the lifetime of the widget.

In this step, you’ll add a stateful widget, `RandomWords`, which creates its `State` class, `_RandomWordsState`. You’ll then use `RandomWords` as a child inside the existing `MyApp` stateless widget.

1. Create the boilerplate code for a stateful widget.  
    In `lib/main.dart`, position your cursor after all of the code, enter **Return** a couple times to start on a fresh line. In your IDE, start typing `stful`. The editor asks if you want to create a `Stateful` widget. Press **Return** to accept. The boilerplate code for two classes appears, and the cursor is positioned for you to enter the name of your stateful widget.
    
2. Enter `RandomWords` as the name of your widget.  
    The `RandomWords` widget does little else beside creating its `State` class.  
      
    Once you’ve entered `RandomWords` as the name of the stateful widget, the IDE automatically updates the accompanying `State` class, naming it `_RandomWordsState`. By default, the name of the `State` class is prefixed with an underbar. Prefixing an identifier with an underscore [enforces privacy](https://dart.dev/guides/language/language-tour#libraries-and-visibility) in the Dart language and is a recommended best practice for `State` objects.  
      
    The IDE also automatically updates the state class to extend `State<RandomWords>`, indicating that you’re using a generic [`State`](https://api.flutter.dev/flutter/widgets/State-class.html) class specialized for use with `RandomWords`. Most of the app’s logic resides here—it maintains the state for the `RandomWords` widget. This class saves the list of generated word pairs, which grows infinitely as the user scrolls and, in part 2 of this lab, favorites word pairs as the user adds or removes them from the list by toggling the heart icon.  
      
    Both classes now look as follows:
    
    
    
    ```
    class RandomWords extends StatefulWidget {
      @override
      _RandomWordsState createState() => _RandomWordsState();
    }
    
    class _RandomWordsState extends State<RandomWords> {
      @override
      Widget build(BuildContext context) {
        return Container();
      }
    }
    ```
    
3. Update the `build()` method in `_RandomWordsState`:
    
    lib/main.dart (\_RandomWordsState)
    
    
    
    class \_RandomWordsState extends State<RandomWords\> { @override Widget build(BuildContext context) {  final wordPair \= WordPair.random();  return Text(wordPair.asPascalCase); } }
    
    After adding the state class, the IDE complains that the class is missing a build method. Next, you’ll add a basic build method that generates the word pairs by moving the word generation code from `MyApp` to `_RandomWordsState`.
    
4. Remove the word generation code from `MyApp` by making the changes shown in the following diff:
    
    {step2\_use\_package → step3\_stateful\_widget}/lib/main.dart
    
    <table class="d2h-diff-table"><tbody class="d2h-diff-tbody"><tr><td class="d2h-code-linenumber d2h-info"></td><td class="d2h-info"><div class="d2h-code-line d2h-info">@@ -10,7 +10,6 @@</div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">10</div><div class="line-num2">10</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MyApp</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatelessWidget</span> </span>{</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">11</div><div class="line-num2">11</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-meta">@override</span></span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">12</div><div class="line-num2">12</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">Widget build(BuildContext context) {</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">13</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-keyword">final</span> wordPair = WordPair.random();</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">14</div><div class="line-num2">13</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-keyword">return</span> MaterialApp(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">15</div><div class="line-num2">14</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">title: <span class="hljs-string">'Welcome to Flutter'</span>,</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">16</div><div class="line-num2">15</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">home: Scaffold(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-info"></td><td class="d2h-info"><div class="d2h-code-line d2h-info">@@ -18,8 +17,8 @@</div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">18</div><div class="line-num2">17</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">title: Text(<span class="hljs-string">'Welcome to Flutter'</span>),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">19</div><div class="line-num2">18</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">20</div><div class="line-num2">19</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">body: Center(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">21</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">child: <del>Text</del>(<del>wordPair.asPascalCase</del>),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-ins"><div class="line-num1"></div><div class="line-num2">20</div></td><td class="d2h-ins"><div class="d2h-code-line d2h-ins"><span class="d2h-code-line-prefix">+</span> <span class="d2h-code-line-ctn hljs dart">child: <ins>RandomWords</ins>(),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">22</div><div class="line-num2">21</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">23</div><div class="line-num2">22</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">24</div><div class="line-num2">23</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">);</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">25</div><div class="line-num2">24</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">}</span></div></td></tr></tbody></table>
    
5. Restart the app. The app should behave as before, displaying a word pairing each time you hot reload or save the app.
    

**Tip:** If you see a warning on a hot reload that you might need to restart the app, consider restarting it. The warning might be a false positive, but restarting your app ensures that your changes are reflected in the app’s UI.

### Problems?

If your app is not running correctly, look for typos. If you want to try some of Flutter’s debugging tools, check out the [DevTools](https://flutter.dev/docs/development/tools/devtools) suite of debugging and profiling tools. If needed, use the code at the following link to get back on track.

- [lib/main.dart](https://raw.githubusercontent.com/flutter/codelabs/master/startup_namer/step3_stateful_widget/lib/main.dart)

## [](https://flutter.dev/docs/get-started/codelab#step-4-create-an-infinite-scrolling-listview)Step 4: Create an infinite scrolling ListView

In this step, you’ll expand `_RandomWordsState` to generate and display a list of word pairings. As the user scrolls the list (displayed in a `ListView` widget) grows infinitely. `ListView`’s `builder` factory constructor allows you to build a list view lazily, on demand.

1. Add a `_suggestions` list to the `_RandomWordsState` class for saving suggested word pairings. Also, add a `_biggerFont` variable for making the font size larger.
    
    lib/main.dart
    
    
    
	```dart 
	class _RandomWordsState extends State<RandomWords\> {
		  final _suggestions = <WordPair>[]; 
		  final _biggerFont = TextStyle(fontSize: 18.0); 
		  // ···
	}
	```
    
    Next, you’ll add a `_buildSuggestions()` function to the `_RandomWordsState` class. This method builds the `ListView` that displays the suggested word pairing.
    
    The `ListView` class provides a builder property, `itemBuilder`, that’s a factory builder and callback function specified as an anonymous function. Two parameters are passed to the function—the `BuildContext`, and the row iterator, `i`. The iterator begins at 0 and increments each time the function is called. It increments twice for every suggested word pairing: once for the ListTile, and once for the Divider. This model allows the suggested list to continue growing as the user scrolls.
    
2. Add a `_buildSuggestions()` function to the `_RandomWordsState` class:
    
    lib/main.dart (\_buildSuggestions)
    ```dart
	Widget _buildSuggestions() { 
		return ListView.builder( 
			padding: EdgeInsets.all(16.0), 
			itemBuilder: \*1\*
				(context, i) {
					if (i.isOdd) return Divider(); 
					\*2\*
					final index = i ~/ 2; 
					\*3\*
					if (index >= _suggestions.length) {
					_suggestions.addAll(generateWordPairs().take(10)); 
						\*4\* 
						} return _buildRow(
						_suggestions[index]); 
						}
						);
						}
	```
    
    1. The `itemBuilder` callback is called once per suggested word pairing, and places each suggestion into a `ListTile` row. For even rows, the function adds a `ListTile` row for the word pairing. For odd rows, the function adds a `Divider` widget to visually separate the entries. Note that the divider might be difficult to see on smaller devices.
    2. Add a one-pixel-high divider widget before each row in the `ListView`.
    3. The expression `i ~/ 2` divides `i` by 2 and returns an integer result. For example: 1, 2, 3, 4, 5 becomes 0, 1, 1, 2, 2. This calculates the actual number of word pairings in the `ListView`, minus the divider widgets.
    4. If you’ve reached the end of the available word pairings, then generate 10 more and add them to the suggestions list.
    
    The `_buildSuggestions()` function calls `_buildRow()` once per word pair. This function displays each new pair in a `ListTile`, which allows you to make the rows more attractive in the next step.
    
3. Add a `_buildRow()` function to `_RandomWordsState`:
    
    lib/main.dart (\_buildRow)
    
    
    
    Widget \_buildRow(WordPair pair) { return ListTile( title: Text( pair.asPascalCase, style: \_biggerFont, ), ); }
    
4. In the `_RandomWordsState` class, update the `build()` method to use `_buildSuggestions()`, rather than directly calling the word generation library. ([`Scaffold`](https://api.flutter.dev/flutter/material/Scaffold-class.html) implements the basic Material Design visual layout.) Replace the method body with the highlighted code:
    
    lib/main.dart (build)
    
    
    
    @override Widget build(BuildContext context) { return Scaffold(  appBar: AppBar(  title: Text('Startup Name Generator'),  ),  body: \_buildSuggestions(), ); }
    
5. In the `MyApp` class, update the `build()` method by changing the title, and changing the home to be a `RandomWords` widget:
    
    {step3\_stateful\_widget → step4\_infinite\_list}/lib/main.dart
    
    <table class="d2h-diff-table"><tbody class="d2h-diff-tbody"><tr><td class="d2h-code-linenumber d2h-info"></td><td class="d2h-info"><div class="d2h-code-line d2h-info">@@ -10,15 +10,8 @@</div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">10</div><div class="line-num2">10</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MyApp</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatelessWidget</span> </span>{</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">11</div><div class="line-num2">11</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-meta">@override</span></span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">12</div><div class="line-num2">12</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">Widget build(BuildContext context) {</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">13</div><div class="line-num2">13</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart"><span class="hljs-keyword">return</span> MaterialApp(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">14</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">title: <span class="hljs-string">'</span><del><span class="hljs-string">Welcome</span></del><span class="hljs-string"> </span><del><span class="hljs-string">to</span></del><span class="hljs-string"> </span><del><span class="hljs-string">Flutter</span></del><span class="hljs-string">'</span>,</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">15</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">home: <del>Scaffold</del>(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-ins"><div class="line-num1"></div><div class="line-num2">14</div></td><td class="d2h-ins"><div class="d2h-code-line d2h-ins"><span class="d2h-code-line-prefix">+</span> <span class="d2h-code-line-ctn hljs dart">title: <span class="hljs-string">'</span><ins><span class="hljs-string">Startup</span></ins><span class="hljs-string"> </span><ins><span class="hljs-string">Name</span></ins><span class="hljs-string"> </span><ins><span class="hljs-string">Generator</span></ins><span class="hljs-string">'</span>,</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-ins"><div class="line-num1"></div><div class="line-num2">15</div></td><td class="d2h-ins"><div class="d2h-code-line d2h-ins"><span class="d2h-code-line-prefix">+</span> <span class="d2h-code-line-ctn hljs dart">home: <ins>RandomWords</ins>(<ins>),</ins></span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">16</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">appBar: AppBar(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">17</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">title: Text(<span class="hljs-string">'Welcome to Flutter'</span>),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">18</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">19</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">body: Center(</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">20</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">child: RandomWords(),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">21</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-del"><div class="line-num1">22</div><div class="line-num2"></div></td><td class="d2h-del"><div class="d2h-code-line d2h-del"><span class="d2h-code-line-prefix">-</span> <span class="d2h-code-line-ctn hljs dart">),</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">23</div><div class="line-num2">16</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">);</span></div></td></tr><tr><td class="d2h-code-linenumber d2h-cntx"><div class="line-num1">24</div><div class="line-num2">17</div></td><td class="d2h-cntx"><div class="d2h-code-line d2h-cntx"><span class="d2h-code-line-prefix">&nbsp;</span> <span class="d2h-code-line-ctn hljs dart">}</span></div></td></tr></tbody></table>
    
6. Restart the app. You should see a list of word pairings no matter how far you scroll.
    
    ![App at completion of fourth step on Android](https://flutter.dev//get-started/android/step4-infinite-list-69f7c62bf16f67eaade07551db4b18b065d6c7a81e042a10cd34d31ecb7f2514.png)
    
    Android
    
    ![App at completion of fourth step on iOS](https://flutter.dev//get-started/ios/step4-infinite-list-70ea9d8fd7191fb3726f1743bb03499815f93df4f42b687cfd7916052c35eb07.png)
    
    iOS
    

### Problems?

If your app is not running correctly, look for typos. If you want to try some of Flutter’s debugging tools, check out the [DevTools](https://flutter.dev/docs/development/tools/devtools) suite of debugging and profiling tools. If needed, use the code at the following link to get back on track.

- [lib/main.dart](https://raw.githubusercontent.com/flutter/codelabs/master/startup_namer/step4_infinite_list/lib/main.dart)

## [](https://flutter.dev/docs/get-started/codelab#profile-or-release-runs)Profile or release runs

**Important:** Do _not_ test the performance of your app with debug and hot reload enabled.

So far you’ve been running your app in _debug_ mode. Debug mode trades performance for useful developer features such as hot reload and step debugging. It’s not unexpected to see slow performance and janky animations in debug mode. Once you are ready to analyze performance or release your app, you’ll want to use Flutter’s “profile” or “release” build modes. For more details, see [Flutter’s build modes](https://flutter.dev/docs/testing/build-modes).

**Important:** If you’re concerned about the package size of your app, see [Measuring your app’s size](https://flutter.dev/docs/perf/app-size).

## Next steps

![The app from part 2](https://flutter.dev//get-started/startup-namer-b85740ef920a57e28524f84e9c06cfb380128d10780e91eaf2c7613a56f3f511.gif)

The app from part 2

Congratulations!

You’ve written an interactive Flutter app that runs on both iOS and Android. In this codelab, you’ve:

- Created a Flutter app from the ground up.
- Written Dart code.
- Leveraged an external, third-party library.
- Used hot reload for a faster development cycle.
- Implemented a stateful widget.
- Created a lazily loaded, infinite scrolling list.

If you would like to extend this app, proceed to [part 2](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2) on the [Google Developers Codelabs](https://codelabs.developers.google.com/) site, where you add the following functionality:

- Implement interactivity by adding a clickable heart icon to save favorite pairings.
- Implement navigation to a new route by adding a new screen containing the saved favorites.
- Modify the theme color, making an all-white app.