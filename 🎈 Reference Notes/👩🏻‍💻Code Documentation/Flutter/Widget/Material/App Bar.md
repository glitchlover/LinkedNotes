inherits : [[Material Library]]
#a_Flutter_class	#Doc-Flutter
# AppBar class

A material design app bar.

An app bar consists of a toolbar and potentially other widgets, such as a [TabBar](https://api.flutter.dev/flutter/material/TabBar-class.html) and a [FlexibleSpaceBar](https://api.flutter.dev/flutter/material/FlexibleSpaceBar-class.html). App bars typically expose one or more common [actions](https://api.flutter.dev/flutter/material/AppBar/actions.html) with [IconButton](https://api.flutter.dev/flutter/material/IconButton-class.html)s which are optionally followed by a [PopupMenuButton](https://api.flutter.dev/flutter/material/PopupMenuButton-class.html) for less common operations (sometimes called the "overflow menu").

App bars are typically used in the [Scaffold.appBar](https://api.flutter.dev/flutter/material/Scaffold/appBar.html) property, which places the app bar as a fixed-height widget at the top of the screen. For a scrollable app bar, see [SliverAppBar](https://api.flutter.dev/flutter/material/SliverAppBar-class.html), which embeds an [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) in a sliver for use in a [CustomScrollView](https://api.flutter.dev/flutter/widgets/CustomScrollView-class.html).

The AppBar displays the toolbar widgets, [leading](https://api.flutter.dev/flutter/material/AppBar/leading.html), [title](https://api.flutter.dev/flutter/material/AppBar/title.html), and [actions](https://api.flutter.dev/flutter/material/AppBar/actions.html), above the [bottom](https://api.flutter.dev/flutter/material/AppBar/bottom.html) (if any). The [bottom](https://api.flutter.dev/flutter/material/AppBar/bottom.html) is usually used for a [TabBar](https://api.flutter.dev/flutter/material/TabBar-class.html). If a [flexibleSpace](https://api.flutter.dev/flutter/material/AppBar/flexibleSpace.html) widget is specified then it is stacked behind the toolbar and the bottom widget. The following diagram shows where each of these slots appears in the toolbar when the writing language is left-to-right (e.g. English):

The [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) insets its content based on the ambient [MediaQuery](https://api.flutter.dev/flutter/widgets/MediaQuery-class.html)'s padding, to avoid system UI intrusions. It's taken care of by [Scaffold](https://api.flutter.dev/flutter/material/Scaffold-class.html) when used in the [Scaffold.appBar](https://api.flutter.dev/flutter/material/Scaffold/appBar.html) property. When animating an [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html), unexpected [MediaQuery](https://api.flutter.dev/flutter/widgets/MediaQuery-class.html) changes (as is common in [Hero](https://api.flutter.dev/flutter/widgets/Hero-class.html) animations) may cause the content to suddenly jump. Wrap the [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) in a [MediaQuery](https://api.flutter.dev/flutter/widgets/MediaQuery-class.html) widget, and adjust its padding such that the animation is smooth.

![The leading widget is in the top left, the actions are in the top right,
the title is between them. The bottom is, naturally, at the bottom, and the
flexibleSpace is behind all of them.](https://flutter.github.io/assets-for-api-docs/assets/material/app_bar.png)

If the [leading](https://api.flutter.dev/flutter/material/AppBar/leading.html) widget is omitted, but the [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) is in a [Scaffold](https://api.flutter.dev/flutter/material/Scaffold-class.html) with a [Drawer](https://api.flutter.dev/flutter/material/Drawer-class.html), then a button will be inserted to open the drawer. Otherwise, if the nearest [Navigator](https://api.flutter.dev/flutter/widgets/Navigator-class.html) has any previous routes, a [BackButton](https://api.flutter.dev/flutter/material/BackButton-class.html) is inserted instead. This behavior can be turned off by setting the [automaticallyImplyLeading](https://api.flutter.dev/flutter/material/AppBar/automaticallyImplyLeading.html) to false. In that case a null leading widget will result in the middle/title widget stretching to start.

[_link_](https://api.flutter.dev/flutter/# "Copy link to clipboard")

var visibleSnippet1 = "longSnippet1"; Interactive App Sample code

This sample shows an [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) with two simple actions. The first action opens a [SnackBar](https://api.flutter.dev/flutter/material/SnackBar-class.html), while the second action navigates to a new page.

To create a local project with this code sample, run:  
flutter create --sample=material.AppBar.1 mysample

This sample shows an [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) with two simple actions. The first action opens a [SnackBar](https://api.flutter.dev/flutter/material/SnackBar-class.html), while the second action navigates to a new page.

_assignment_

```dart
final GlobalKey<ScaffoldState> scaffoldKey = GlobalKey<ScaffoldState>();
final SnackBar snackBar = const SnackBar(content: Text('Showing Snackbar'));

void openPage(BuildContext context) {
  Navigator.push(context, MaterialPageRoute(
    builder: (BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          title: const Text('Next page'),
        ),
        body: const Center(
          child: Text(
            'This is the next page',
            style: TextStyle(fontSize: 24),
          ),
        ),
      );
    },
  ));
}

// ...

Widget build(BuildContext context) {
  return Scaffold(
    key: scaffoldKey,
    appBar: AppBar(
      title: const Text('AppBar Demo'),
      actions: <Widget>[
        IconButton(
          icon: const Icon(Icons.add_alert),
          tooltip: 'Show Snackbar',
          onPressed: () {
            scaffoldKey.currentState.showSnackBar(snackBar);
          },
        ),
        IconButton(
          icon: const Icon(Icons.navigate_next),
          tooltip: 'Next page',
          onPressed: () {
            openPage(context);
          },
        ),
      ],
    ),
    body: const Center(
      child: Text(
        'This is the home page',
        style: TextStyle(fontSize: 24),
      ),
    ),
  );
}
```

See also:

- [Scaffold](https://api.flutter.dev/flutter/material/Scaffold-class.html), which displays the [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) in its [Scaffold.appBar](https://api.flutter.dev/flutter/material/Scaffold/appBar.html) slot.
- [SliverAppBar](https://api.flutter.dev/flutter/material/SliverAppBar-class.html), which uses [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) to provide a flexible app bar that can be used in a [CustomScrollView](https://api.flutter.dev/flutter/widgets/CustomScrollView-class.html).
- [TabBar](https://api.flutter.dev/flutter/material/TabBar-class.html), which is typically placed in the [bottom](https://api.flutter.dev/flutter/material/AppBar/bottom.html) slot of the [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html) if the screen has multiple pages arranged in tabs.
- [IconButton](https://api.flutter.dev/flutter/material/IconButton-class.html), which is used with [actions](https://api.flutter.dev/flutter/material/AppBar/actions.html) to show buttons on the app bar.
- [PopupMenuButton](https://api.flutter.dev/flutter/material/PopupMenuButton-class.html), to show a popup menu on the app bar, via [actions](https://api.flutter.dev/flutter/material/AppBar/actions.html).
- [FlexibleSpaceBar](https://api.flutter.dev/flutter/material/FlexibleSpaceBar-class.html), which is used with [flexibleSpace](https://api.flutter.dev/flutter/material/AppBar/flexibleSpace.html) when the app bar can expand and collapse.
- [material.io/design/components/app-bars-top.html](https://material.io/design/components/app-bars-top.html)

Inheritance

- [Object](https://api.flutter.dev/flutter/dart-core/Object-class.html)
- [DiagnosticableTree](https://api.flutter.dev/flutter/foundation/DiagnosticableTree-class.html)
- [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)
- [StatefulWidget](https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html)
- AppBar

Implemented types

- [PreferredSizeWidget](https://api.flutter.dev/flutter/widgets/PreferredSizeWidget-class.html)

## Constructors

[AppBar](https://api.flutter.dev/flutter/material/AppBar/AppBar.html)({[Key](https://api.flutter.dev/flutter/foundation/Key-class.html) key, [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html) leading, [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html) automaticallyImplyLeading: true, [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html) title, [List](https://api.flutter.dev/flutter/dart-core/List-class.html)<[Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)\> actions, [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html) flexibleSpace, [PreferredSizeWidget](https://api.flutter.dev/flutter/widgets/PreferredSizeWidget-class.html) bottom, [double](https://api.flutter.dev/flutter/dart-core/double-class.html) elevation, [Color](https://api.flutter.dev/flutter/dart-ui/Color-class.html) shadowColor, [ShapeBorder](https://api.flutter.dev/flutter/painting/ShapeBorder-class.html) shape, [Color](https://api.flutter.dev/flutter/dart-ui/Color-class.html) backgroundColor, [Brightness](https://api.flutter.dev/flutter/dart-ui/Brightness-class.html) brightness, [IconThemeData](https://api.flutter.dev/flutter/widgets/IconThemeData-class.html) iconTheme, [IconThemeData](https://api.flutter.dev/flutter/widgets/IconThemeData-class.html) actionsIconTheme, [TextTheme](https://api.flutter.dev/flutter/material/TextTheme-class.html) textTheme, [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html) primary: true, [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html) centerTitle, [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html) excludeHeaderSemantics: false, [double](https://api.flutter.dev/flutter/dart-core/double-class.html) titleSpacing: NavigationToolbar.kMiddleSpacing, [double](https://api.flutter.dev/flutter/dart-core/double-class.html) toolbarOpacity: 1.0, [double](https://api.flutter.dev/flutter/dart-core/double-class.html) bottomOpacity: 1.0, [double](https://api.flutter.dev/flutter/dart-core/double-class.html) toolbarHeight})

Creates a material design app bar. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/AppBar.html)

## Properties

[actions](https://api.flutter.dev/flutter/material/AppBar/actions.html) → [List](https://api.flutter.dev/flutter/dart-core/List-class.html)<[Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)\>

Widgets to display in a row after the [title](https://api.flutter.dev/flutter/material/AppBar/title.html) widget. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/actions.html)

final

[actionsIconTheme](https://api.flutter.dev/flutter/material/AppBar/actionsIconTheme.html) → [IconThemeData](https://api.flutter.dev/flutter/widgets/IconThemeData-class.html)

The color, opacity, and size to use for the icons that appear in the app bar's [actions](https://api.flutter.dev/flutter/material/AppBar/actions.html). This should only be used when the [actions](https://api.flutter.dev/flutter/material/AppBar/actions.html) should be themed differently than the icon that appears in the app bar's [leading](https://api.flutter.dev/flutter/material/AppBar/leading.html) widget. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/actionsIconTheme.html)

final

[automaticallyImplyLeading](https://api.flutter.dev/flutter/material/AppBar/automaticallyImplyLeading.html) → [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html)

Controls whether we should try to imply the leading widget if null. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/automaticallyImplyLeading.html)

final

[backgroundColor](https://api.flutter.dev/flutter/material/AppBar/backgroundColor.html) → [Color](https://api.flutter.dev/flutter/dart-ui/Color-class.html)

The color to use for the app bar's material. Typically this should be set along with [brightness](https://api.flutter.dev/flutter/material/AppBar/brightness.html), [iconTheme](https://api.flutter.dev/flutter/material/AppBar/iconTheme.html), [textTheme](https://api.flutter.dev/flutter/material/AppBar/textTheme.html). [\[...\]](https://api.flutter.dev/flutter/material/AppBar/backgroundColor.html)

final

[bottom](https://api.flutter.dev/flutter/material/AppBar/bottom.html) → [PreferredSizeWidget](https://api.flutter.dev/flutter/widgets/PreferredSizeWidget-class.html)

This widget appears across the bottom of the app bar. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/bottom.html)

final

[bottomOpacity](https://api.flutter.dev/flutter/material/AppBar/bottomOpacity.html) → [double](https://api.flutter.dev/flutter/dart-core/double-class.html)

How opaque the bottom part of the app bar is. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/bottomOpacity.html)

final

[brightness](https://api.flutter.dev/flutter/material/AppBar/brightness.html) → [Brightness](https://api.flutter.dev/flutter/dart-ui/Brightness-class.html)

The brightness of the app bar's material. Typically this is set along with [backgroundColor](https://api.flutter.dev/flutter/material/AppBar/backgroundColor.html), [iconTheme](https://api.flutter.dev/flutter/material/AppBar/iconTheme.html), [textTheme](https://api.flutter.dev/flutter/material/AppBar/textTheme.html). [\[...\]](https://api.flutter.dev/flutter/material/AppBar/brightness.html)

final

[centerTitle](https://api.flutter.dev/flutter/material/AppBar/centerTitle.html) → [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html)

Whether the title should be centered. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/centerTitle.html)

final

[elevation](https://api.flutter.dev/flutter/material/AppBar/elevation.html) → [double](https://api.flutter.dev/flutter/dart-core/double-class.html)

The z-coordinate at which to place this app bar relative to its parent. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/elevation.html)

final

[excludeHeaderSemantics](https://api.flutter.dev/flutter/material/AppBar/excludeHeaderSemantics.html) → [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html)

Whether the title should be wrapped with header [Semantics](https://api.flutter.dev/flutter/widgets/Semantics-class.html). [\[...\]](https://api.flutter.dev/flutter/material/AppBar/excludeHeaderSemantics.html)

final

[flexibleSpace](https://api.flutter.dev/flutter/material/AppBar/flexibleSpace.html) → [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)

This widget is stacked behind the toolbar and the tab bar. It's height will be the same as the app bar's overall height. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/flexibleSpace.html)

final

[hashCode](https://api.flutter.dev/flutter/widgets/Widget/hashCode.html) → [int](https://api.flutter.dev/flutter/dart-core/int-class.html)

The hash code for this object. [\[...\]](https://api.flutter.dev/flutter/widgets/Widget/hashCode.html)

@nonVirtual, read-only, inherited

[iconTheme](https://api.flutter.dev/flutter/material/AppBar/iconTheme.html) → [IconThemeData](https://api.flutter.dev/flutter/widgets/IconThemeData-class.html)

The color, opacity, and size to use for app bar icons. Typically this is set along with [backgroundColor](https://api.flutter.dev/flutter/material/AppBar/backgroundColor.html), [brightness](https://api.flutter.dev/flutter/material/AppBar/brightness.html), [textTheme](https://api.flutter.dev/flutter/material/AppBar/textTheme.html). [\[...\]](https://api.flutter.dev/flutter/material/AppBar/iconTheme.html)

final

[key](https://api.flutter.dev/flutter/widgets/Widget/key.html) → [Key](https://api.flutter.dev/flutter/foundation/Key-class.html)

Controls how one widget replaces another widget in the tree. [\[...\]](https://api.flutter.dev/flutter/widgets/Widget/key.html)

final, inherited

[leading](https://api.flutter.dev/flutter/material/AppBar/leading.html) → [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)

A widget to display before the [title](https://api.flutter.dev/flutter/material/AppBar/title.html). [\[...\]](https://api.flutter.dev/flutter/material/AppBar/leading.html)

final

[preferredSize](https://api.flutter.dev/flutter/material/AppBar/preferredSize.html) → [Size](https://api.flutter.dev/flutter/dart-ui/Size-class.html)

A size whose height is the sum of [toolbarHeight](https://api.flutter.dev/flutter/material/AppBar/toolbarHeight.html) and the [bottom](https://api.flutter.dev/flutter/material/AppBar/bottom.html) widget's preferred height. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/preferredSize.html)

final

[primary](https://api.flutter.dev/flutter/material/AppBar/primary.html) → [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html)

Whether this app bar is being displayed at the top of the screen. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/primary.html)

final

[runtimeType](https://api.flutter.dev/flutter/dart-core/Object/runtimeType.html) → [Type](https://api.flutter.dev/flutter/dart-core/Type-class.html)

A representation of the runtime type of the object.

read-only, inherited

[shadowColor](https://api.flutter.dev/flutter/material/AppBar/shadowColor.html) → [Color](https://api.flutter.dev/flutter/dart-ui/Color-class.html)

The color to paint the shadow below the app bar. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/shadowColor.html)

final

[shape](https://api.flutter.dev/flutter/material/AppBar/shape.html) → [ShapeBorder](https://api.flutter.dev/flutter/painting/ShapeBorder-class.html)

The material's shape as well its shadow. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/shape.html)

final

[textTheme](https://api.flutter.dev/flutter/material/AppBar/textTheme.html) → [TextTheme](https://api.flutter.dev/flutter/material/TextTheme-class.html)

The typographic styles to use for text in the app bar. Typically this is set along with [brightness](https://api.flutter.dev/flutter/material/AppBar/brightness.html) [backgroundColor](https://api.flutter.dev/flutter/material/AppBar/backgroundColor.html), [iconTheme](https://api.flutter.dev/flutter/material/AppBar/iconTheme.html). [\[...\]](https://api.flutter.dev/flutter/material/AppBar/textTheme.html)

final

[title](https://api.flutter.dev/flutter/material/AppBar/title.html) → [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)

The primary widget displayed in the app bar. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/title.html)

final

[titleSpacing](https://api.flutter.dev/flutter/material/AppBar/titleSpacing.html) → [double](https://api.flutter.dev/flutter/dart-core/double-class.html)

The spacing around [title](https://api.flutter.dev/flutter/material/AppBar/title.html) content on the horizontal axis. This spacing is applied even if there is no [leading](https://api.flutter.dev/flutter/material/AppBar/leading.html) content or [actions](https://api.flutter.dev/flutter/material/AppBar/actions.html). If you want [title](https://api.flutter.dev/flutter/material/AppBar/title.html) to take all the space available, set this value to 0.0. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/titleSpacing.html)

final

[toolbarHeight](https://api.flutter.dev/flutter/material/AppBar/toolbarHeight.html) → [double](https://api.flutter.dev/flutter/dart-core/double-class.html)

Defines the height of the toolbar component of an [AppBar](https://api.flutter.dev/flutter/material/AppBar-class.html). [\[...\]](https://api.flutter.dev/flutter/material/AppBar/toolbarHeight.html)

final

[toolbarOpacity](https://api.flutter.dev/flutter/material/AppBar/toolbarOpacity.html) → [double](https://api.flutter.dev/flutter/dart-core/double-class.html)

How opaque the toolbar part of the app bar is. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/toolbarOpacity.html)

final

## Methods

[createElement](https://api.flutter.dev/flutter/widgets/StatefulWidget/createElement.html)() → [StatefulElement](https://api.flutter.dev/flutter/widgets/StatefulElement-class.html) 

Creates a [StatefulElement](https://api.flutter.dev/flutter/widgets/StatefulElement-class.html) to manage this widget's location in the tree. [\[...\]](https://api.flutter.dev/flutter/widgets/StatefulWidget/createElement.html)

inherited

[createState](https://api.flutter.dev/flutter/material/AppBar/createState.html)() → \_AppBarState 

Creates the mutable state for this widget at a given location in the tree. [\[...\]](https://api.flutter.dev/flutter/material/AppBar/createState.html)

override

[debugDescribeChildren](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/debugDescribeChildren.html)() → [List](https://api.flutter.dev/flutter/dart-core/List-class.html)<[DiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticsNode-class.html)\> 

Returns a list of [DiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticsNode-class.html) objects describing this node's children. [\[...\]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/debugDescribeChildren.html)

@protected, inherited

[debugFillProperties](https://api.flutter.dev/flutter/widgets/Widget/debugFillProperties.html)([DiagnosticPropertiesBuilder](https://api.flutter.dev/flutter/foundation/DiagnosticPropertiesBuilder-class.html) properties) → void 

Add additional properties associated with the node. [\[...\]](https://api.flutter.dev/flutter/widgets/Widget/debugFillProperties.html)

inherited

[noSuchMethod](https://api.flutter.dev/flutter/dart-core/Object/noSuchMethod.html)([Invocation](https://api.flutter.dev/flutter/dart-core/Invocation-class.html) invocation) → dynamic 

Invoked when a non-existent method or property is accessed. [\[...\]](https://api.flutter.dev/flutter/dart-core/Object/noSuchMethod.html)

inherited

[toDiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toDiagnosticsNode.html)({[String](https://api.flutter.dev/flutter/dart-core/String-class.html) name, [DiagnosticsTreeStyle](https://api.flutter.dev/flutter/foundation/DiagnosticsTreeStyle-class.html) style}) → [DiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticsNode-class.html) 

Returns a debug representation of the object that is used by debugging tools and by [DiagnosticsNode.toStringDeep](https://api.flutter.dev/flutter/foundation/DiagnosticsNode/toStringDeep.html). [\[...\]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toDiagnosticsNode.html)

inherited

[toString](https://api.flutter.dev/flutter/foundation/Diagnosticable/toString.html)({[DiagnosticLevel](https://api.flutter.dev/flutter/foundation/DiagnosticLevel-class.html) minLevel: DiagnosticLevel.info}) → [String](https://api.flutter.dev/flutter/dart-core/String-class.html) 

Returns a string representation of this object.

inherited

[toStringDeep](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringDeep.html)({[String](https://api.flutter.dev/flutter/dart-core/String-class.html) prefixLineOne: '', [String](https://api.flutter.dev/flutter/dart-core/String-class.html) prefixOtherLines, [DiagnosticLevel](https://api.flutter.dev/flutter/foundation/DiagnosticLevel-class.html) minLevel: DiagnosticLevel.debug}) → [String](https://api.flutter.dev/flutter/dart-core/String-class.html) 

Returns a string representation of this node and its descendants. [\[...\]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringDeep.html)

inherited

[toStringShallow](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringShallow.html)({[String](https://api.flutter.dev/flutter/dart-core/String-class.html) joiner: ', ', [DiagnosticLevel](https://api.flutter.dev/flutter/foundation/DiagnosticLevel-class.html) minLevel: DiagnosticLevel.debug}) → [String](https://api.flutter.dev/flutter/dart-core/String-class.html) 

Returns a one-line detailed description of the object. [\[...\]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringShallow.html)

inherited

[toStringShort](https://api.flutter.dev/flutter/widgets/Widget/toStringShort.html)() → [String](https://api.flutter.dev/flutter/dart-core/String-class.html) 

A short, textual description of this widget.

inherited

## Operators

[operator ==](https://api.flutter.dev/flutter/widgets/Widget/operator_equals.html)([Object](https://api.flutter.dev/flutter/dart-core/Object-class.html) other) → [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html) 

The equality operator. [\[...\]](https://api.flutter.dev/flutter/widgets/Widget/operator_equals.html)

@nonVirtual, inherited