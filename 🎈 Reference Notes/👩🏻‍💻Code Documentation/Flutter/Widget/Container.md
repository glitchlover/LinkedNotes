# Container class

A convenience widget that combines common painting, positioning, and sizing widgets.

A container first surrounds the child with [padding](https://api.flutter.dev/flutter/widgets/Container/padding.html) (inflated by any borders present in the [decoration](https://api.flutter.dev/flutter/widgets/Container/decoration.html)) and then applies additional [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html) to the padded extent (incorporating the `width` and `height` as constraints, if either is non-null). The container is then surrounded by additional empty space described from the [margin](https://api.flutter.dev/flutter/widgets/Container/margin.html).

During painting, the container first applies the given [transform](https://api.flutter.dev/flutter/widgets/Container/transform.html), then paints the [decoration](https://api.flutter.dev/flutter/widgets/Container/decoration.html) to fill the padded extent, then it paints the child, and finally paints the [foregroundDecoration](https://api.flutter.dev/flutter/widgets/Container/foregroundDecoration.html), also filling the padded extent.

Containers with no children try to be as big as possible unless the incoming constraints are unbounded, in which case they try to be as small as possible. Containers with children size themselves to their children. The `width`, `height`, and [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html) arguments to the constructor override this.

By default, containers return false for all hit tests. If the [color](https://api.flutter.dev/flutter/widgets/Container/color.html) property is specified, the hit testing is handled by [ColoredBox](https://api.flutter.dev/flutter/widgets/ColoredBox-class.html), which always returns true. If the [decoration](https://api.flutter.dev/flutter/widgets/Container/decoration.html) or [foregroundDecoration](https://api.flutter.dev/flutter/widgets/Container/foregroundDecoration.html) properties are specified, hit testing is handled by [Decoration.hitTest](https://api.flutter.dev/flutter/painting/Decoration/hitTest.html).

## Layout behavior

_See [BoxConstraints](https://api.flutter.dev/flutter/rendering/BoxConstraints-class.html) for an introduction to box layout models._

Since [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) combines a number of other widgets each with their own layout behavior, [Container](https://api.flutter.dev/flutter/widgets/Container-class.html)'s layout behavior is somewhat complicated.

Summary: [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) tries, in order: to honor [alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html), to size itself to the [child](https://api.flutter.dev/flutter/widgets/Container/child.html), to honor the `width`, `height`, and [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html), to expand to fit the parent, to be as small as possible.

More specifically:

If the widget has no child, no `height`, no `width`, no [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html), and the parent provides unbounded constraints, then [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) tries to size as small as possible.

If the widget has no child and no [alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html), but a `height`, `width`, or [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html) are provided, then the [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) tries to be as small as possible given the combination of those constraints and the parent's constraints.

If the widget has no child, no `height`, no `width`, no [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html), and no [alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html), but the parent provides bounded constraints, then [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) expands to fit the constraints provided by the parent.

If the widget has an [alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html), and the parent provides unbounded constraints, then the [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) tries to size itself around the child.

If the widget has an [alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html), and the parent provides bounded constraints, then the [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) tries to expand to fit the parent, and then positions the child within itself as per the [alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html).

Otherwise, the widget has a [child](https://api.flutter.dev/flutter/widgets/Container/child.html) but no `height`, no `width`, no [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html), and no [alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html), and the [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) passes the constraints from the parent to the child and sizes itself to match the child.

The [margin](https://api.flutter.dev/flutter/widgets/Container/margin.html) and [padding](https://api.flutter.dev/flutter/widgets/Container/padding.html) properties also affect the layout, as described in the documentation for those properties. (Their effects merely augment the rules described above.) The [decoration](https://api.flutter.dev/flutter/widgets/Container/decoration.html) can implicitly increase the [padding](https://api.flutter.dev/flutter/widgets/Container/padding.html) (e.g. borders in a [BoxDecoration](https://api.flutter.dev/flutter/painting/BoxDecoration-class.html) contribute to the [padding](https://api.flutter.dev/flutter/widgets/Container/padding.html)); see [Decoration.padding](https://api.flutter.dev/flutter/painting/Decoration/padding.html).

## Example

[_link_](https://api.flutter.dev/flutter/# "Copy link to clipboard")

Sample

This example shows a 48x48 amber square (placed inside a [Center](https://api.flutter.dev/flutter/widgets/Center-class.html) widget in case the parent widget has its own opinions regarding the size that the [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) should take), with a margin so that it stays away from neighboring widgets:

![An amber colored container with the dimensions of 48 square pixels.](https://flutter.github.io/assets-for-api-docs/assets/widgets/container_a.png)

_assignment_

```dart
Center(
  child: Container(
    margin: const EdgeInsets.all(10.0),
    color: Colors.amber[600],
    width: 48.0,
    height: 48.0,
  ),
)
```

[_link_](https://api.flutter.dev/flutter/# "Copy link to clipboard")

Sample

This example shows how to use many of the features of [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) at once. The [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html) are set to fit the font size plus ample headroom vertically, while expanding horizontally to fit the parent. The [padding](https://api.flutter.dev/flutter/widgets/Container/padding.html) is used to make sure there is space between the contents and the text. The [color](https://api.flutter.dev/flutter/widgets/Container/color.html) makes the box blue. The [alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html) causes the [child](https://api.flutter.dev/flutter/widgets/Container/child.html) to be centered in the box. Finally, the [transform](https://api.flutter.dev/flutter/widgets/Container/transform.html) applies a slight rotation to the entire contraption to complete the effect.

![A blue rectangular container with 'Hello World' in the center, rotated
slightly in the z axis.](https://flutter.github.io/assets-for-api-docs/assets/widgets/container_b.png)

_assignment_

```dart
Container(
  constraints: BoxConstraints.expand(
    height: Theme.of(context).textTheme.headline4.fontSize * 1.1 + 200.0,
  ),
  padding: const EdgeInsets.all(8.0),
  color: Colors.blue[600],
  alignment: Alignment.center,
  child: Text('Hello World',
    style: Theme.of(context)
        .textTheme
        .headline4
        .copyWith(color: Colors.white)),
  transform: Matrix4.rotationZ(0.1),
)
```

See also:

- [AnimatedContainer](https://api.flutter.dev/flutter/widgets/AnimatedContainer-class.html), a variant that smoothly animates the properties when they change.
- [Border](https://api.flutter.dev/flutter/painting/Border-class.html), which has a sample which uses [Container](https://api.flutter.dev/flutter/widgets/Container-class.html) heavily.
- [Ink](https://api.flutter.dev/flutter/material/Ink-class.html), which paints a [Decoration](https://api.flutter.dev/flutter/painting/Decoration-class.html) on a [Material](https://api.flutter.dev/flutter/material/Material-class.html), allowing [InkResponse](https://api.flutter.dev/flutter/material/InkResponse-class.html) and [InkWell](https://api.flutter.dev/flutter/material/InkWell-class.html) splashes to paint over them.
- The [catalog of layout widgets](https://flutter.dev/widgets/layout/).

Inheritance

- [Object](https://api.flutter.dev/flutter/dart-core/Object-class.html)
- [DiagnosticableTree](https://api.flutter.dev/flutter/foundation/DiagnosticableTree-class.html)
- [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)
- [StatelessWidget](https://api.flutter.dev/flutter/widgets/StatelessWidget-class.html)
- Container

## Constructors

[Container](https://api.flutter.dev/flutter/widgets/Container/Container.html)({[Key](https://api.flutter.dev/flutter/foundation/Key-class.html) key, [AlignmentGeometry](https://api.flutter.dev/flutter/painting/AlignmentGeometry-class.html) alignment, [EdgeInsetsGeometry](https://api.flutter.dev/flutter/painting/EdgeInsetsGeometry-class.html) padding, [Color](https://api.flutter.dev/flutter/dart-ui/Color-class.html) color, [Decoration](https://api.flutter.dev/flutter/painting/Decoration-class.html) decoration, [Decoration](https://api.flutter.dev/flutter/painting/Decoration-class.html) foregroundDecoration, [double](https://api.flutter.dev/flutter/dart-core/double-class.html) width, [double](https://api.flutter.dev/flutter/dart-core/double-class.html) height, [BoxConstraints](https://api.flutter.dev/flutter/rendering/BoxConstraints-class.html) constraints, [EdgeInsetsGeometry](https://api.flutter.dev/flutter/painting/EdgeInsetsGeometry-class.html) margin, [Matrix4](https://api.flutter.dev/flutter/vector_math_64/Matrix4-class.html) transform, [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html) child, [Clip](https://api.flutter.dev/flutter/dart-ui/Clip-class.html) clipBehavior: Clip.none})

Creates a widget that combines common painting, positioning, and sizing widgets. [\[...\]](https://api.flutter.dev/flutter/widgets/Container/Container.html)

## Properties

[alignment](https://api.flutter.dev/flutter/widgets/Container/alignment.html) → [AlignmentGeometry](https://api.flutter.dev/flutter/painting/AlignmentGeometry-class.html)

Align the [child](https://api.flutter.dev/flutter/widgets/Container/child.html) within the container. [\[...\]](https://api.flutter.dev/flutter/widgets/Container/alignment.html)

final

[child](https://api.flutter.dev/flutter/widgets/Container/child.html) → [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)

The [child](https://api.flutter.dev/flutter/widgets/Container/child.html) contained by the container. [\[...\]](https://api.flutter.dev/flutter/widgets/Container/child.html)

final

[clipBehavior](https://api.flutter.dev/flutter/widgets/Container/clipBehavior.html) → [Clip](https://api.flutter.dev/flutter/dart-ui/Clip-class.html)

The clip behavior when [Container.decoration](https://api.flutter.dev/flutter/widgets/Container/decoration.html) has a clipPath. [\[...\]](https://api.flutter.dev/flutter/widgets/Container/clipBehavior.html)

final

[color](https://api.flutter.dev/flutter/widgets/Container/color.html) → [Color](https://api.flutter.dev/flutter/dart-ui/Color-class.html)

The color to paint behind the [child](https://api.flutter.dev/flutter/widgets/Container/child.html). [\[...\]](https://api.flutter.dev/flutter/widgets/Container/color.html)

final

[constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html) → [BoxConstraints](https://api.flutter.dev/flutter/rendering/BoxConstraints-class.html)

Additional constraints to apply to the child. [\[...\]](https://api.flutter.dev/flutter/widgets/Container/constraints.html)

final

[decoration](https://api.flutter.dev/flutter/widgets/Container/decoration.html) → [Decoration](https://api.flutter.dev/flutter/painting/Decoration-class.html)

The decoration to paint behind the [child](https://api.flutter.dev/flutter/widgets/Container/child.html). [\[...\]](https://api.flutter.dev/flutter/widgets/Container/decoration.html)

final

[foregroundDecoration](https://api.flutter.dev/flutter/widgets/Container/foregroundDecoration.html) → [Decoration](https://api.flutter.dev/flutter/painting/Decoration-class.html)

The decoration to paint in front of the [child](https://api.flutter.dev/flutter/widgets/Container/child.html).

final

[hashCode](https://api.flutter.dev/flutter/widgets/Widget/hashCode.html) → [int](https://api.flutter.dev/flutter/dart-core/int-class.html)

The hash code for this object. [\[...\]](https://api.flutter.dev/flutter/widgets/Widget/hashCode.html)

@nonVirtual, read-only, inherited

[key](https://api.flutter.dev/flutter/widgets/Widget/key.html) → [Key](https://api.flutter.dev/flutter/foundation/Key-class.html)

Controls how one widget replaces another widget in the tree. [\[...\]](https://api.flutter.dev/flutter/widgets/Widget/key.html)

final, inherited

[margin](https://api.flutter.dev/flutter/widgets/Container/margin.html) → [EdgeInsetsGeometry](https://api.flutter.dev/flutter/painting/EdgeInsetsGeometry-class.html)

Empty space to surround the [decoration](https://api.flutter.dev/flutter/widgets/Container/decoration.html) and [child](https://api.flutter.dev/flutter/widgets/Container/child.html).

final

[padding](https://api.flutter.dev/flutter/widgets/Container/padding.html) → [EdgeInsetsGeometry](https://api.flutter.dev/flutter/painting/EdgeInsetsGeometry-class.html)

Empty space to inscribe inside the [decoration](https://api.flutter.dev/flutter/widgets/Container/decoration.html). The [child](https://api.flutter.dev/flutter/widgets/Container/child.html), if any, is placed inside this padding. [\[...\]](https://api.flutter.dev/flutter/widgets/Container/padding.html)

final

[runtimeType](https://api.flutter.dev/flutter/dart-core/Object/runtimeType.html) → [Type](https://api.flutter.dev/flutter/dart-core/Type-class.html)

A representation of the runtime type of the object.

read-only, inherited

[transform](https://api.flutter.dev/flutter/widgets/Container/transform.html) → [Matrix4](https://api.flutter.dev/flutter/vector_math_64/Matrix4-class.html)

The transformation matrix to apply before painting the container.

final

## Methods

[build](https://api.flutter.dev/flutter/widgets/Container/build.html)([BuildContext](https://api.flutter.dev/flutter/widgets/BuildContext-class.html) context) → [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html) 

Describes the part of the user interface represented by this widget. [\[...\]](https://api.flutter.dev/flutter/widgets/Container/build.html)

override

[createElement](https://api.flutter.dev/flutter/widgets/StatelessWidget/createElement.html)() → [StatelessElement](https://api.flutter.dev/flutter/widgets/StatelessElement-class.html) 

Creates a [StatelessElement](https://api.flutter.dev/flutter/widgets/StatelessElement-class.html) to manage this widget's location in the tree. [\[...\]](https://api.flutter.dev/flutter/widgets/StatelessWidget/createElement.html)

inherited

[debugDescribeChildren](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/debugDescribeChildren.html)() → [List](https://api.flutter.dev/flutter/dart-core/List-class.html)<[DiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticsNode-class.html)\> 

Returns a list of [DiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticsNode-class.html) objects describing this node's children. [\[...\]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/debugDescribeChildren.html)

@protected, inherited

[debugFillProperties](https://api.flutter.dev/flutter/widgets/Container/debugFillProperties.html)([DiagnosticPropertiesBuilder](https://api.flutter.dev/flutter/foundation/DiagnosticPropertiesBuilder-class.html) properties) → void 

Add additional properties associated with the node. [\[...\]](https://api.flutter.dev/flutter/widgets/Container/debugFillProperties.html)

override

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