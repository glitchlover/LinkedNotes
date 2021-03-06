# Layouts in Flutter

1. [Docs](https://flutter.dev/docs) 
2. [Development](https://flutter.dev/docs/development) 
3. [UI](https://flutter.dev/docs/development/ui) 
4. [Layout](https://flutter.dev/docs/development/ui/layout) 


#### What's the point?

- Widgets are classes used to build UIs.
- Widgets are used for both layout and UI elements.
- Compose simple widgets to build complex widgets.

The core of Flutter’s [[layout]] mechanism is widgets. In Flutter, almost everything is a widget—even layout models are widgets. The images, icons, and text that you see in a Flutter app are all widgets. But things you don’t see are also widgets, such as the rows, columns, and grids that arrange, constrain, and align the visible widgets.

You create a layout by composing widgets to build more complex widgets. For example, the first screenshot below shows 3 icons with a label under each one:

![Sample layout](https://flutter.dev/assets/ui/layout/lakes-icons-9e75d63c8af0fc5ddf026c71b3e85687548ec29f2f1e06f8e78c546969a21127.png) ![Sample layout with visual debugging](https://flutter.dev/assets/ui/layout/lakes-icons-visual-f9e45691d76ba85d4ea2160941f42c8a2ce1a17d41d6e6aac8f3feb89e679f99.png)

The second screenshot displays the visual layout, showing a row of 3 columns where each column contains an icon and a label.

**Note:** Most of the screenshots in this tutorial are displayed with `debugPaintSizeEnabled` set to true so you can see the visual layout. For more information, see [Debugging layout issues visually](https://flutter.dev/docs/development/tools/devtools/inspector#debugging-layout-issues-visually), a section in [Using the Flutter inspector](https://flutter.dev/docs/development/tools/devtools/inspector).

Here’s a diagram of the widget tree for this UI:

![Node tree](https://flutter.dev/assets/ui/layout/sample-flutter-layout-46c76f6ab08f94fa4204469dbcf6548a968052af102ae5a1ae3c78bc24e0d915.png)

Most of this should look as you might expect, but you might be wondering about the containers (shown in pink). [[Container]] is a widget class that allows you to customize its child widget. Use a `Container` when you want to add padding, margins, borders, or background color, to name some of its capabilities.

In this example, each [`Text`](https://api.flutter.dev/flutter/widgets/Text-class.html) widget is placed in a `Container` to add margins. The entire [`Row`](https://api.flutter.dev/flutter/widgets/Row-class.html) is also placed in a `Container` to add padding around the row.
The rest of the UI in this example is controlled by properties. Set an [`Icon`](https://api.flutter.dev/flutter/material/Icons-class.html)’s color using its `color` property. Use the `Text.style` property to set the font, its color, weight, and so on. Columns and rows have properties that allow you to specify how their children are aligned vertically or horizontally, and how much space the children should occupy.

## Lay out a widget

How do you layout a single widget in Flutter? This section shows you how to create and display a simple widget. It also shows the entire code for a simple Hello World app.

In Flutter, it takes only a few steps to put text, an icon, or an image on the screen.

### Select a layout widget

Choose from a variety of [layout widgets](https://flutter.dev/docs/development/ui/widgets/layout) based on how you want to align or constrain the visible widget, as these characteristics are typically passed on to the contained widget.

This example uses [`Center`](https://api.flutter.dev/flutter/widgets/Center-class.html) which centers its content horizontally and vertically.

### Create a visible widget

For example, create a [`Text`](https://api.flutter.dev/flutter/widgets/Text-class.html) widget:



Text('Hello World'),

Create an [`Image`](https://api.flutter.dev/flutter/widgets/Image-class.html) widget:



Image.asset( 'images/lake.jpg', fit: BoxFit.cover, ),

Create an [`Icon`](https://api.flutter.dev/flutter/material/Icons-class.html) widget:



Icon( Icons.star, color: Colors.red\[500\], ),

### 3\. Add the visible widget to the layout widget

All layout widgets have either of the following:

- A `child` property if they take a single child—for example, `Center` or `Container`
- A `children` property if they take a list of widgets—for example, `Row`, `Column`, `ListView`, or `Stack`.

Add the `Text` widget to the `Center` widget:



Center( child: Text('Hello World'), ),

### 4\. Add the layout widget to the page

A Flutter app is itself a widget, and most widgets have a [`build()`](https://api.flutter.dev/flutter/widgets/StatelessWidget/build.html) method. Instantiating and returning a widget in the app’s `build()` method displays the widget.

#### material-apps)Material apps

For a `Material` app, you can use a [`Scaffold`](https://api.flutter.dev/flutter/material/Scaffold-class.html) widget; it provides a default banner, background color, and has API for adding drawers, snack bars, and bottom sheets. Then you can add the `Center` widget directly to the `body` property for the home page.

lib/main.dart (MyApp)



class MyApp extends StatelessWidget { @override Widget build(BuildContext context) { return MaterialApp( title: 'Flutter layout demo', home: Scaffold( appBar: AppBar( title: Text('Flutter layout demo'), ), body: Center( child: Text('Hello World'), ), ), ); } }

**Note:** The [Material library](https://api.flutter.dev/flutter/material/material-library.html) implements widgets that follow [Material Design](https://material.io/design) principles. When designing your UI, you can exclusively use widgets from the standard [widgets library](https://api.flutter.dev/flutter/widgets/widgets-library.html), or you can use widgets from the Material library. You can mix widgets from both libraries, you can customize existing widgets, or you can build your own set of custom widgets.

#### non-material-apps)Non-Material apps

For a non-Material app, you can add the `Center` widget to the app’s `build()` method:

lib/main.dart (MyApp)



class MyApp extends StatelessWidget { @override Widget build(BuildContext context) { return Container( decoration: BoxDecoration(color: Colors.white), child: Center( child: Text( 'Hello World', textDirection: TextDirection.ltr, style: TextStyle( fontSize: 32, color: Colors.black87, ), ), ), ); } }

By default a non-Material app doesn’t include an `AppBar`, title, or background color. If you want these features in a non-Material app, you have to build them yourself. This app changes the background color to white and the text to dark grey to mimic a Material app.

That’s it! When you run the app, you should see _Hello World_.

App source code:

- [Material app](https://github.com/flutter/website/tree/master/examples/layout/base)
- [Non-Material app](https://github.com/flutter/website/tree/master/examples/layout/non_material)

![Hello World](https://flutter.dev/assets/ui/layout/hello-world-4ad7a5134f8a38ced291e606a3be4db84b00f68c357af9fefd2732d2cc8bb067.png)

-

## Lay out multiple widgets vertically and horizontally

One of the most common layout patterns is to arrange widgets vertically or horizontally. You can use a `Row` widget to arrange widgets horizontally, and a `Column` widget to arrange widgets vertically.

#### What's the point?

- `Row` and `Column` are two of the most commonly used layout patterns.
- `Row` and `Column` each take a list of child widgets.
- A child widget can itself be a `Row`, `Column`, or other complex widget.
- You can specify how a `Row` or `Column` aligns its children, both vertically and horizontally.
- You can stretch or constrain specific child widgets.
- You can specify how child widgets use the `Row`’s or `Column`’s available space.

To create a row or column in Flutter, you add a list of children widgets to a [`Row`](https://api.flutter.dev/flutter/widgets/Row-class.html) or [`Column`](https://api.flutter.dev/flutter/widgets/Column-class.html) widget. In turn, each child can itself be a row or column, and so on. The following example shows how it is possible to nest rows or columns inside of rows or columns.

This layout is organized as a `Row`. The row contains two children: a column on the left, and an image on the right:

![Screenshot with callouts showing the row containing two children](https://flutter.dev/assets/ui/layout/pavlova-diagram-8b3d410640d9b3575d69c0724203c5dff6814fdd1a57546a5f65f98254077a92.png)

The left column’s widget tree nests rows and columns.

![Diagram showing a left column broken down to its sub-rows and sub-columns](https://flutter.dev/assets/ui/layout/pavlova-left-column-diagram-c9bf1a39b39270615ce8e82608952ac3edaa0d1eab8691f8783e6408fdfbdfb3.png)

You’ll implement some of Pavlova’s layout code in [Nesting rows and columns](https://flutter.dev/docs/developmentnesting-rows-and-columns).

**Note:** `Row` and `Column` are basic primitive widgets for horizontal and vertical layouts—these low-level widgets allow for maximum customization. Flutter also offers specialized, higher level widgets that might be sufficient for your needs. For example, instead of `Row` you might prefer [`ListTile`](https://api.flutter.dev/flutter/material/ListTile-class.html), an easy-to-use widget with properties for leading and trailing icons, and up to 3 lines of text. Instead of Column, you might prefer [`ListView`](https://api.flutter.dev/flutter/widgets/ListView-class.html), a column-like layout that automatically scrolls if its content is too long to fit the available space. For more information, see [Common layout widgets](https://flutter.dev/docs/developmentcommon-layout-widgets).

### Aligning widgets

You control how a row or column aligns its children using the `mainAxisAlignment` and `crossAxisAlignment` properties. For a row, the main axis runs horizontally and the cross axis runs vertically. For a column, the main axis runs vertically and the cross axis runs horizontally.

![Diagram showing the main axis and cross axis for a row](https://flutter.dev/assets/ui/layout/row-diagram-ad51795e19e3e1d412815b287c9caa694ad357892e3ab8b3ef1da0c4c6e011db.png) ![Diagram showing the main axis and cross axis for a column](https://flutter.dev/assets/ui/layout/column-diagram-4e2ce8e33c32a09d090280fb7b2925baaf58f6de7876a551c207ab904e2fafc6.png)

The [`MainAxisAlignment`](https://api.flutter.dev/flutter/rendering/MainAxisAlignment-class.html) and [`CrossAxisAlignment`](https://api.flutter.dev/flutter/rendering/CrossAxisAlignment-class.html) classes offer a variety of constants for controlling alignment.

**Note:** When you add images to your project, you need to update the `pubspec.yaml` file to access them—this example uses `Image.asset` to display the images. For more information, see this example’s [`pubspec.yaml` file](https://github.com/flutter/website/tree/master/examples/layout/row_column/pubspec.yaml) or [Adding assets and images](https://flutter.dev/docs/development/ui/assets-and-images). You don’t need to do this if you’re referencing online images using `Image.network`.

In the following example, each of the 3 images is 100 pixels wide. The render box (in this case, the entire screen) is more than 300 pixels wide, so setting the main axis alignment to `spaceEvenly` divides the free horizontal space evenly between, before, and after each image.



Row( mainAxisAlignment: MainAxisAlignment.spaceEvenly, children: \[ Image.asset('images/pic1.jpg'), Image.asset('images/pic2.jpg'), Image.asset('images/pic3.jpg'), \], );

![Row with 3 evenly spaced images](https://flutter.dev/assets/ui/layout/row-spaceevenly-visual-bae00ee7fc0b8a0fbe46d74b113f9f0e4e4942e55609cf263cefca81f986d871.png)

**App source:** [row\_column](https://github.com/flutter/website/tree/master/examples/layout/row_column)

Columns work the same way as rows. The following example shows a column of 3 images, each is 100 pixels high. The height of the render box (in this case, the entire screen) is more than 300 pixels, so setting the main axis alignment to `spaceEvenly` divides the free vertical space evenly between, above, and below each image.



Column( mainAxisAlignment: MainAxisAlignment.spaceEvenly, children: \[ Image.asset('images/pic1.jpg'), Image.asset('images/pic2.jpg'), Image.asset('images/pic3.jpg'), \], );

**App source:** [row\_column](https://github.com/flutter/website/tree/master/examples/layout/row_column)

![Column showing 3 images spaced evenly](https://flutter.dev/assets/ui/layout/column-visual-075205bae7b5e6e5ee7be85a1a3ded9bdb52319b41c75d83710c0216d4084904.png)

### Sizing widgets

When a layout is too large to fit a device, a yellow and black striped pattern appears along the affected edge. Here is an [example](https://github.com/flutter/website/tree/master/examples/layout/sizing) of a row that is too wide:

![Overly-wide row](https://flutter.dev/assets/ui/layout/layout-too-large-f97b9d98cbac9a793c4190a6542ef8f31820a92610afcc387400d1fe30358e18.png)

Widgets can be sized to fit within a row or column by using the [`Expanded`](https://api.flutter.dev/flutter/widgets/Expanded-class.html) widget. To fix the previous example where the row of images is too wide for its render box, wrap each image with an `Expanded` widget.



Row( crossAxisAlignment: CrossAxisAlignment.center, children: \[ Expanded( child: Image.asset('images/pic1.jpg'), ), Expanded( child: Image.asset('images/pic2.jpg'), ), Expanded( child: Image.asset('images/pic3.jpg'), ), \], );

![Row of 3 images that are too wide, but each is constrained to take only 1/3 of the space](https://flutter.dev/assets/ui/layout/row-expanded-2-visual-7003ec3a27b38a2cc925b97abfd933fe6d2fce62494400e0e3c9790b715cd0d1.png)

**App source:** [sizing](https://github.com/flutter/website/tree/master/examples/layout/sizing)

Perhaps you want a widget to occupy twice as much space as its siblings. For this, use the `Expanded` widget `flex` property, an integer that determines the flex factor for a widget. The default flex factor is 1. The following code sets the flex factor of the middle image to 2:



Row( crossAxisAlignment: CrossAxisAlignment.center, children: \[ Expanded( child: Image.asset('images/pic1.jpg'), ), Expanded( flex: 2, child: Image.asset('images/pic2.jpg'), ), Expanded( child: Image.asset('images/pic3.jpg'), ), \], );

![Row of 3 images with the middle image twice as wide as the others](https://flutter.dev/assets/ui/layout/row-expanded-visual-fa9a01df7b96ba5cb33162b91369658fea86554139953e3cc0357de83281133d.png)

**App source:** [sizing](https://github.com/flutter/website/tree/master/examples/layout/sizing)

### Packing widgets

By default, a row or column occupies as much space along its main axis as possible, but if you want to pack the children closely together, set its `mainAxisSize` to `MainAxisSize.min`. The following example uses this property to pack the star icons together.



Row( mainAxisSize: MainAxisSize.min, children: \[ Icon(Icons.star, color: Colors.green\[500\]), Icon(Icons.star, color: Colors.green\[500\]), Icon(Icons.star, color: Colors.green\[500\]), Icon(Icons.star, color: Colors.black), Icon(Icons.star, color: Colors.black), \], )

![Row of 5 stars, packed together in the middle of the row](https://flutter.dev/assets/ui/layout/packed-5583166ea8f018a2c3c829cb075eb63b465cf859e74ae1d7792d2c50813e32aa.png)

**App source:** [pavlova](https://github.com/flutter/website/tree/master/examples/layout/pavlova)

### Nesting rows and columns

The layout framework allows you to nest rows and columns inside of rows and columns as deeply as you need. Let’s look at the code for the outlined section of the following layout:

![Screenshot of the pavlova app, with the ratings and icon rows outlined in red](https://flutter.dev/assets/ui/layout/pavlova-large-annotated-05a910e84242ba5185fe735515cb3f794640f49493036631ec99f768dce107c6.png)

The outlined section is implemented as two rows. The ratings row contains five stars and the number of reviews. The icons row contains three columns of icons and text.

The widget tree for the ratings row:

![Ratings row widget tree](https://flutter.dev/assets/ui/layout/widget-tree-pavlova-rating-row-7555ca5c12948715086787af2783d2e489e44117928b798f4c5d05bb8bec5119.png)

The `ratings` variable creates a row containing a smaller row of 5 star icons, and text:



var stars \= Row( mainAxisSize: MainAxisSize.min, children: \[ Icon(Icons.star, color: Colors.green\[500\]), Icon(Icons.star, color: Colors.green\[500\]), Icon(Icons.star, color: Colors.green\[500\]), Icon(Icons.star, color: Colors.black), Icon(Icons.star, color: Colors.black), \], ); final ratings \= Container( padding: EdgeInsets.all(20), child: Row( mainAxisAlignment: MainAxisAlignment.spaceEvenly, children: \[ stars, Text( '170 Reviews', style: TextStyle( color: Colors.black, fontWeight: FontWeight.w800, fontFamily: 'Roboto', letterSpacing: 0.5, fontSize: 20, ), ), \], ), );

**Tip:** To minimize the visual confusion that can result from heavily nested layout code, implement pieces of the UI in variables and functions.

The icons row, below the ratings row, contains 3 columns; each column contains an icon and two lines of text, as you can see in its widget tree:

![Icon widget tree](https://flutter.dev/assets/ui/layout/widget-tree-pavlova-icon-row-f3c4d7f703df25139611c19d59877196fb4292b10ded60066ceeca974402dc2f.png)

The `iconList` variable defines the icons row:



final descTextStyle \= TextStyle( color: Colors.black, fontWeight: FontWeight.w800, fontFamily: 'Roboto', letterSpacing: 0.5, fontSize: 18, height: 2, ); // DefaultTextStyle.merge() allows you to create a default text // style that is inherited by its child and all subsequent children. final iconList \= DefaultTextStyle.merge( style: descTextStyle, child: Container( padding: EdgeInsets.all(20), child: Row( mainAxisAlignment: MainAxisAlignment.spaceEvenly, children: \[ Column( children: \[ Icon(Icons.kitchen, color: Colors.green\[500\]), Text('PREP:'), Text('25 min'), \], ), Column( children: \[ Icon(Icons.timer, color: Colors.green\[500\]), Text('COOK:'), Text('1 hr'), \], ), Column( children: \[ Icon(Icons.restaurant, color: Colors.green\[500\]), Text('FEEDS:'), Text('4-6'), \], ), \], ), ), );

The `leftColumn` variable contains the ratings and icons rows, as well as the title and text that describes the Pavlova:



final leftColumn \= Container( padding: EdgeInsets.fromLTRB(20, 30, 20, 20), child: Column( children: \[ titleText, subTitle, ratings, iconList, \], ), );

The left column is placed in a `Container` to constrain its width. Finally, the UI is constructed with the entire row (containing the left column and the image) inside a `Card`.

The [Pavlova image](https://pixabay.com/en/photos/pavlova) is from [Pixabay](https://pixabay.com/en/photos/pavlova). You can embed an image from the net using `Image.network()` but, for this example, the image is saved to an images directory in the project, added to the [pubspec file](https://github.com/flutter/website/tree/master/examples/layout/pavlova/pubspec.yaml), and accessed using `Images.asset()`. For more information, see [Adding assets and images](https://flutter.dev/docs/development/ui/assets-and-images).



body: Center( child: Container( margin: EdgeInsets.fromLTRB(0, 40, 0, 30), height: 600, child: Card( child: Row( crossAxisAlignment: CrossAxisAlignment.start, children: \[ Container( width: 440, child: leftColumn, ), mainImage, \], ), ), ), ),

**Tip:** The Pavlova example runs best horizontally on a wide device, such as a tablet. If you are running this example in the iOS simulator, you can select a different device using the **Hardware > Device** menu. For this example, we recommend the iPad Pro. You can change its orientation to landscape mode using **Hardware > Rotate**. You can also change the size of the simulator window (without changing the number of logical pixels) using **Window > Scale**.

**App source:** [pavlova](https://github.com/flutter/website/tree/master/examples/layout/pavlova)

-

## Common layout widgets

Flutter has a rich library of layout widgets. Here are a few of those most commonly used. The intent is to get you up and running as quickly as possible, rather than overwhelm you with a complete list. For information on other available widgets, refer to the [Widget catalog](https://flutter.dev/docs/development/ui/widgets), or use the Search box in the [API reference docs](https://api.flutter.dev/flutter). Also, the widget pages in the API docs often make suggestions about similar widgets that might better suit your needs.

The following widgets fall into two categories: standard widgets from the [widgets library](https://api.flutter.dev/flutter/widgets/widgets-library.html), and specialized widgets from the [Material library](https://api.flutter.dev/flutter/material/material-library.html). Any app can use the widgets library but only Material apps can use the Material Components library.

### Standard widgets

- [`Container`](https://flutter.dev/docs/developmentcontainer): Adds padding, margins, borders, background color, or other decorations to a widget.
- [`GridView`](https://flutter.dev/docs/developmentgridview): Lays widgets out as a scrollable grid.
- [`ListView`](https://flutter.dev/docs/developmentlistview): Lays widgets out as a scrollable list.
- [`Stack`](https://flutter.dev/docs/developmentstack): Overlaps a widget on top of another.

### Material widgets

- [`Card`](https://flutter.dev/docs/developmentcard): Organizes related info into a box with rounded corners and a drop shadow.
- [`ListTile`](https://flutter.dev/docs/developmentlisttile): Organizes up to 3 lines of text, and optional leading and trailing icons, into a row.

### Container

Many layouts make liberal use of [`Container`](https://api.flutter.dev/flutter/widgets/Container-class.html)s to separate widgets using padding, or to add borders or margins. You can change the device’s background by placing the entire layout into a `Container` and changing its background color or image.

#### Summary (Container)

- Add padding, margins, borders
- Change background color or image
- Contains a single child widget, but that child can be a Row, Column, or even the root of a widget tree

![Diagram showing: margin, border, padding, and content](https://flutter.dev/assets/ui/layout/margin-padding-border-9616dd0d7af45b95e6fcface25cd933b6b4a0fda51c1ab1bb9287bc8ed92c356.png)

#### Examples (Container)

This layout consists of a column with two rows, each containing 2 images. A [`Container`](https://api.flutter.dev/flutter/widgets/Container-class.html) is used to change the background color of the column to a lighter grey.



Widget \_buildImageColumn() \=> Container( decoration: BoxDecoration( color: Colors.black26, ), child: Column( children: \[ \_buildImageRow(1), \_buildImageRow(3), \], ), );

![Screenshot showing 2 rows, each containing 2 images](https://flutter.dev/assets/ui/layout/container-c31fce287ed0d6c2b0de32af625b2351bd8a08c236a2e60578f940c7b4aceece.png)

A `Container` is also used to add a rounded border and margins to each image:



Widget \_buildDecoratedImage(int imageIndex) \=> Expanded( child: Container( decoration: BoxDecoration( border: Border.all(width: 10, color: Colors.black38), borderRadius: const BorderRadius.all(const Radius.circular(8)), ), margin: const EdgeInsets.all(4), child: Image.asset('images/pic$imageIndex.jpg'), ), ); Widget \_buildImageRow(int imageIndex) \=> Row( children: \[ \_buildDecoratedImage(imageIndex), \_buildDecoratedImage(imageIndex + 1), \], );

You can find more `Container` examples in the [tutorial](https://flutter.dev/docs/development/ui/layout/tutorial) and the Flutter Gallery ([running app](https://flutter.github.io/gallery/#/), [repo](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery)).

**App source:** [container](https://github.com/flutter/website/tree/master/examples/layout/container)

-

### GridView

Use [`GridView`](https://api.flutter.dev/flutter/widgets/GridView-class.html) to lay widgets out as a two-dimensional list. `GridView` provides two pre-fabricated lists, or you can build your own custom grid. When a `GridView` detects that its contents are too long to fit the render box, it automatically scrolls.

#### Summary (GridView)

- Lays widgets out in a grid
- Detects when the column content exceeds the render box and automatically provides scrolling
- Build your own custom grid, or use one of the provided grids:
    - `GridView.count` allows you to specify the number of columns
    - `GridView.extent` allows you to specify the maximum pixel width of a tile

**Note:** When displaying a two-dimensional list where it’s important which row and column a cell occupies (for example, it’s the entry in the “calorie” column for the “avocado” row), use [`Table`](https://api.flutter.dev/flutter/widgets/Table-class.html) or [`DataTable`](https://api.flutter.dev/flutter/material/DataTable-class.html).

#### Examples (GridView)

![A 3-column grid of photos](https://flutter.dev/assets/ui/layout/gridview-extent-b36976ff50ecc7d55518fa41c10ac3d6de2c0e8a19d550e607461b46e8722395.png)

Uses `GridView.extent` to create a grid with tiles a maximum 150 pixels wide.

**App source:** [grid\_and\_list](https://github.com/flutter/website/tree/master/examples/layout/grid_and_list)

![A 2 column grid with footers](https://flutter.dev/assets/ui/layout/gridview-count-flutter-gallery-59cdc10fb37f423463da914fe4c298b00f46d8d70f584080898939b9568df44b.png)

Uses `GridView.count` to create a grid that’s 2 tiles wide in portrait mode, and 3 tiles wide in landscape mode. The titles are created by setting the `footer` property for each [`GridTile`](https://api.flutter.dev/flutter/material/GridTile-class.html).

**Dart code:** [grid\_list\_demo.dart](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery/lib/demo/material/grid_list_demo.dart) from the [Flutter Gallery](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery)



Widget \_buildGrid() \=> GridView.extent( maxCrossAxisExtent: 150, padding: const EdgeInsets.all(4), mainAxisSpacing: 4, crossAxisSpacing: 4, children: \_buildGridTileList(30)); // The images are saved with names pic0.jpg, pic1.jpg...pic29.jpg. // The List.generate() constructor allows an easy way to create // a list when objects have a predictable naming pattern. List<Container\> \_buildGridTileList(int count) \=> List.generate( count, (i) \=> Container(child: Image.asset('images/pic$i.jpg')));

-

### ListView

[`ListView`](https://api.flutter.dev/flutter/widgets/ListView-class.html), a column-like widget, automatically provides scrolling when its content is too long for its render box.

#### Summary (ListView)

- A specialized [`Column`](https://api.flutter.dev/flutter/widgets/Column-class.html) for organizing a list of boxes
- Can be laid out horizontally or vertically
- Detects when its content won’t fit and provides scrolling
- Less configurable than `Column`, but easier to use and supports scrolling

#### Examples (ListView)

![ListView containing movie theaters and restaurants](https://flutter.dev/assets/ui/layout/listview-34918a738b5d18af88d16a8773e563a3b97f2ffd2710304c5543f8541cbd1345.png)

Uses `ListView` to display a list of businesses using `ListTile`s. A `Divider` separates the theaters from the restaurants.

**App source:** [grid\_and\_list](https://github.com/flutter/website/tree/master/examples/layout/grid_and_list)

![ListView containing shades of blue](https://flutter.dev/assets/ui/layout/listview-flutter-gallery-bac5e59b369906556451d427ef42502b1710fcf34a38d4fb0dc409c14a423548.png)

Uses `ListView` to display the [`Colors`](https://api.flutter.dev/flutter/material/Colors-class.html) from the [Material Design palette](https://material.io/guidelines/style/color.html) for a particular color family.

**Dart code:** [colors\_demo.dart](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery/lib/demo/colors_demo.dart) from the [Flutter Gallery](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery)



Widget \_buildList() \=> ListView( children: \[ \_tile('CineArts at the Empire', '85 W Portal Ave', Icons.theaters), \_tile('The Castro Theater', '429 Castro St', Icons.theaters), \_tile('Alamo Drafthouse Cinema', '2550 Mission St', Icons.theaters), \_tile('Roxie Theater', '3117 16th St', Icons.theaters), \_tile('United Artists Stonestown Twin', '501 Buckingham Way', Icons.theaters), \_tile('AMC Metreon 16', '135 4th St #3000', Icons.theaters), Divider(), \_tile('K\\'s Kitchen', '757 Monterey Blvd', Icons.restaurant), \_tile('Emmy\\'s Restaurant', '1923 Ocean Ave', Icons.restaurant), \_tile( 'Chaiya Thai Restaurant', '272 Claremont Blvd', Icons.restaurant), \_tile('La Ciccia', '291 30th St', Icons.restaurant), \], ); ListTile \_tile(String title, String subtitle, IconData icon) \=> ListTile( title: Text(title, style: TextStyle( fontWeight: FontWeight.w500, fontSize: 20, )), subtitle: Text(subtitle), leading: Icon( icon, color: Colors.blue\[500\], ), );

-

### Stack

Use [`Stack`](https://api.flutter.dev/flutter/widgets/Stack-class.html) to arrange widgets on top of a base widget—often an image. The widgets can completely or partially overlap the base widget.

#### Summary (Stack)

- Use for widgets that overlap another widget
- The first widget in the list of children is the base widget; subsequent children are overlaid on top of that base widget
- A `Stack`’s content can’t scroll
- You can choose to clip children that exceed the render box

#### Examples (Stack)

![Circular avatar image with a label](https://flutter.dev/assets/ui/layout/stack-8b743fe7d0f5fe7e58e3a257572f4b48b1552194f7e3f3ffa15a87edaf99a749.png)

Uses `Stack` to overlay a `Container` (that displays its `Text` on a translucent black background) on top of a `CircleAvatar`. The `Stack` offsets the text using the `alignment` property and `Alignment`s.

**App source:** [card\_and\_stack](https://github.com/flutter/website/tree/master/examples/layout/card_and_stack)

![An image with a grey gradient across the top](https://flutter.dev/assets/ui/layout/stack-flutter-gallery-a90ac4d0242afcd79a8c1e155a6f930ce53960fad61e389108bc73f3f2149e40.png)

Uses `Stack` to overlay a gradient to the top of the image. The gradient ensures that the toolbar’s icons are distinct against the image.

**Dart code:** [contacts\_demo.dart](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery/lib/demo/contacts_demo.dart) from the [Flutter Gallery](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery)



Widget \_buildStack() \=> Stack( alignment: const Alignment(0.6, 0.6), children: \[ CircleAvatar( backgroundImage: AssetImage('images/pic.jpg'), radius: 100, ), Container( decoration: BoxDecoration( color: Colors.black45, ), child: Text( 'Mia B', style: TextStyle( fontSize: 20, fontWeight: FontWeight.bold, color: Colors.white, ), ), ), \], );

-

### Card

A [`Card`](https://api.flutter.dev/flutter/material/Card-class.html), from the [Material library](https://api.flutter.dev/flutter/material/material-library.html), contains related nuggets of information and can be composed from almost any widget, but is often used with [`ListTile`](https://api.flutter.dev/flutter/material/ListTile-class.html). `Card` has a single child, but its child can be a column, row, list, grid, or other widget that supports multiple children. By default, a `Card` shrinks its size to 0 by 0 pixels. You can use [`SizedBox`](https://api.flutter.dev/flutter/widgets/SizedBox-class.html) to constrain the size of a card.

In Flutter, a `Card` features slightly rounded corners and a drop shadow, giving it a 3D effect. Changing a `Card`’s `elevation` property allows you to control the drop shadow effect. Setting the elevation to 24, for example, visually lifts the `Card` further from the surface and causes the shadow to become more dispersed. For a list of supported elevation values, see [Elevation](https://material.io/design/environment/elevation.html) in the [Material guidelines](https://material.io/design). Specifying an unsupported value disables the drop shadow entirely.

#### Summary (Card)

- Implements a [Material card](https://material.io/design/components/cards.html)
- Used for presenting related nuggets of information
- Accepts a single child, but that child can be a `Row`, `Column`, or other widget that holds a list of children
- Displayed with rounded corners and a drop shadow
- A `Card`’s content can’t scroll
- From the [Material library](https://api.flutter.dev/flutter/material/material-library.html)

#### Examples (Card)

![Card containing 3 ListTiles](https://flutter.dev/assets/ui/layout/card-3db18421d33c96f34f8d19889a5f28c61287063a62c9770f311fd56aeff0b364.png)

A `Card` containing 3 ListTiles and sized by wrapping it with a `SizedBox`. A `Divider` separates the first and second `ListTiles`.

**App source:** [card\_and\_stack](https://github.com/flutter/website/tree/master/examples/layout/card_and_stack)

![Card containing an image, text and buttons](https://flutter.dev/assets/ui/layout/card-flutter-gallery-184963eb23d8824ef3df612a6b40205ed113e7c00da98fa22228cc6e6f619d88.png)

A `Card` containing an image and text.

**Dart code:** [cards\_demo.dart](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery/lib/demo/material/cards_demo.dart) from the [Flutter Gallery](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery)



Widget \_buildCard() \=> SizedBox( height: 210, child: Card( child: Column( children: \[ ListTile( title: Text('1625 Main Street', style: TextStyle(fontWeight: FontWeight.w500)), subtitle: Text('My City, CA 99984'), leading: Icon( Icons.restaurant\_menu, color: Colors.blue\[500\], ), ), Divider(), ListTile( title: Text('(408) 555-1212', style: TextStyle(fontWeight: FontWeight.w500)), leading: Icon( Icons.contact\_phone, color: Colors.blue\[500\], ), ), ListTile( title: Text('costa@example.com'), leading: Icon( Icons.contact\_mail, color: Colors.blue\[500\], ), ), \], ), ), );

-

### listtile)ListTile

Use [`ListTile`](https://api.flutter.dev/flutter/material/ListTile-class.html), a specialized row widget from the [Material library](https://api.flutter.dev/flutter/material/material-library.html), for an easy way to create a row containing up to 3 lines of text and optional leading and trailing icons. `ListTile` is most commonly used in [`Card`](https://api.flutter.dev/flutter/material/Card-class.html) or [`ListView`](https://api.flutter.dev/flutter/widgets/ListView-class.html), but can be used elsewhere.

#### Summary (ListTile)

- A specialized row that contains up to 3 lines of text and optional icons
- Less configurable than `Row`, but easier to use
- From the [Material library](https://api.flutter.dev/flutter/material/material-library.html)

#### Examples (ListTile)

![Card containing 3 ListTiles](https://flutter.dev/assets/ui/layout/card-3db18421d33c96f34f8d19889a5f28c61287063a62c9770f311fd56aeff0b364.png)

A `Card` containing 3 `ListTiles`.

**App source:** [card\_and\_stack](https://github.com/flutter/website/tree/master/examples/layout/card_and_stack)

![3 ListTiles, each containing a pull-down button](https://flutter.dev/assets/ui/layout/listtile-flutter-gallery-5d28c96af0ea49816b8ea14bbdb65e3116bc342978627f491ed3697895ab34a5.png)

Uses `ListTile` to list 3 drop down button types.  
**Dart code:** [buttons\_demo.dart](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery/lib/demo/material/buttons_demo.dart) from the [Flutter Gallery](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery)

-

## Constraints

To fully understand Flutter’s layout system, you need to learn how Flutter positions and sizes the components in a layout. For more information, see [Understanding constraints](https://flutter.dev/docs/development/ui/layout/constraints).

## Videos

The following videos, part of the [Flutter in Focus](https://www.youtube.com/watch?v=wgTBLj7rMPM&list=PLjxrf2q8roU2HdJQDjJzOeO6J3FoFLWr2) series, explain `Stateless` and `Stateful` widgets.

[Flutter in Focus playlist](https://www.youtube.com/watch?v=wgTBLj7rMPM&list=PLjxrf2q8roU2HdJQDjJzOeO6J3FoFLWr2)

-

Each episode of the [Widget of the Week series](https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG) focuses on a widget. Several of them includes layout widgets.

[Flutter Widget of the Week playlist](https://www.youtube.com/watch?v=yI-8QHpGIP4&index=5&list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG)

## Other resources

The following resources might help when writing layout code.

- [Layout tutorial](https://flutter.dev/docs/development/ui/layout/tutorial)
    
    Learn how to build a layout.
    
- [Widget catalog](https://flutter.dev/docs/development/ui/widgets)
    
    Describes many of the widgets available in Flutter.
    
- [HTML/CSS Analogs in Flutter](https://flutter.dev/docs/get-started/flutter-for/web-devs)
    
    For those familiar with web programming, this page maps HTML/CSS functionality to Flutter features.
    
- Flutter Gallery [running app](https://flutter.github.io/gallery/#/), [repo](https://github.com/flutter/flutter/tree/master/dev/integration_tests/flutter_gallery)
    
    Demo app showcasing many Material Design widgets and other Flutter features.
    
- [API reference docs](https://api.flutter.dev/flutter)
    
    Reference documentation for all of the Flutter libraries.
    
- [Dealing with Box Constraints in Flutter](https://flutter.dev/docs/development/ui/layout/box-constraints)
    
    Discusses how widgets are constrained by their render boxes.
    
- [Adding assets and images](https://flutter.dev/docs/development/ui/assets-and-images)
    
    Explains how to add images and other assets to your app’s package.
    
- [Zero to One with Flutter](https://medium.com/@mravn/zero-to-one-with-flutter-43b13fd7b354)
    
    One person’s experience writing his first Flutter app.