#Note-Java #need-retouch #important

https://www.dummies.com/programming/java/java-for-dummies-cheat-sheet/

> When doing anything with Java, you need to know your Java words — those programming words, phrases, and nonsense terms that have specific meaning in the Java language, and that get it to do its thing.

# Java For Dummies Cheat Sheet - dummies
2.  [Programming](https://www.dummies.com/programming/)
3.  [Java](https://www.dummies.com/programming/java/)
4.  Java For Dummies Cheat Sheet

When doing anything with Java, you need to know your Java words — those programming words, phrases, and nonsense terms that have specific meaning in the Java language, and that get it to do its thing.

The Words in a Java Program
---------------------------

When you write a Java program, you can divide the program’s words into several categories. This cheat sheet tells you all about those categories.

Keywords
--------

The Java programming language has 50 _keywords_. Each keyword has a specific meaning in the language. You can’t use a keyword for anything other than its pre-assigned meaning.

The following table lists Java’s keywords.

### What It Does

#### `abstract`

Indicates that the details of a class, a method, or an interface are given elsewhere in the code.

#### `assert`

Tests the truth of a condition that the programmer believes is true.

#### `boolean`

Indicates that a value is either true or false.

#### `break`

Jumps out of a loop or switch.

#### `byte`

Indicates that a value is an 8-bit whole number.

#### `case`

Introduces one of several possible paths of execution in a switch statement.

#### `catch`

Introduces statements that are executed when something interrupts the flow of execution in a try clause.

#### `char`

Indicates that a value is a character (a single letter, digit, punctuation symbol, and so on) stored in 16 bits of memory.

#### `class`

Introduces a class — a blueprint for an object.

#### `const`

You can’t use this word in a Java program. The word has no meaning but, because it’s a keyword, you can’t create a variable named `const`.

#### `continue`

Forces the abrupt end of the current loop iteration and begins another iteration.

#### `default`

Introduces a path of execution to take when no case is a match in a switch statement.

#### `do`

Causes the computer to repeat some statements over and over again (for instance, as long as the computer keeps getting unacceptable results).

#### `double`

Indicates that a value is a 64-bit number with one or more digits after the decimal point.

#### `else`

Introduces statements that are executed when the condition in an if statement isn’t true.

#### `enum`

Creates a newly defined type — a group of values that a variable can have.

#### `extends`

Creates a subclass @@md a class that reuses functionality from a previously defined class.

#### `final`

Indicates that a variable’s value cannot be changed, that a class’s functionality cannot be extended, or that a method cannot be overridden.

#### `finally`

Introduces the last will and testament of the statements in a try clause.

#### `float`

Indicates that a value is a 32-bit number with one or more digits after the decimal point.

#### `for`

Gets the computer to repeat some statements over and over again (for instance, a certain number of times).

#### `goto`

You can’t use this word in a Java program. The word has no meaning. Because it’s a keyword, you can’t create a variable named `goto`.

#### `if`

Tests to see whether a condition is true. If it’s true, the computer executes certain statements; otherwise, the computer executes other statements.

#### `implements`

Indicates that a class provides bodies for methods whose headers are declared in an interface.

#### `import`

Enables the programmer to abbreviate the names of classes defined in a package.

#### `instanceof`

Tests to see whether a certain object comes from a certain class.

#### `int`

Indicates that a value is a 32-bit whole number.

#### `interface`

Introduces an interface. An interface is like a class but, for the most part, an interface’s methods have no bodies.

#### `long`

Indicates that a value is a 64-bit whole number.

#### `native`

Enables the programmer to use code that was written in a language other than Java.

#### `new`

Creates an object from an existing class.

#### `package`

Puts the code into a package — a collection of logically related definitions.

#### `private`

Indicates that a variable or method can be used only within a certain class.

#### `protected`

Indicates that a variable or method can be used in subclasses from another package.

#### `public`

Indicates that a variable, class, or method can be used by any other Java code.

#### `return`

Ends execution of a method and possibly returns a value to the calling code.

short

Indicates that a value is a 16-bit whole number.

static

Indicates that a variable or method belongs to a class, rather than to any object created from the class.

#### `strictfp`

Limits the computer’s ability to represent extra large or extra small numbers when the computer does intermediate calculations on float and double values.

#### `super`

Refers to the superclass of the code in which the word super appears.

switch

Tells the computer to follow one of many possible paths of execution (one of many possible cases), depending on the value of an expression.

synchronized

Keeps two threads from interfering with one another.

this

A self-reference — refers to the object in which the word this appears.

throw

Creates a new exception object and indicates that an exceptional situation (usually something unwanted) has occurred.

throws

Indicates that a method or constructor may pass the buck when an exception is thrown.

transient

Indicates that, if and when an object is serialized, a variable’s value doesn’t need to be stored.

try

Introduces statements that are watched (during runtime) for things that can go wrong.

void

Indicates that a method doesn’t return a value.

volatile

Imposes strict rules on the use of a variable by more than one thread at a time.

while

Repeats some statements over and over again (as long as a condition is still true).

Literals
--------

In addition to its keywords, three of the words you use in a Java program are called _literals_. Each literal has a specific meaning in the language. You can’t use a literal for anything other than its pre-assigned meaning.

The following table lists Java’s literal words.

**Literal**

### **What It Does**

#### false

One of the two values that a boolean expression can possibly have.

#### null

The “nothing” value. If you intend to have an expression refer to an object of some kind, but the expression doesn’t refer to any object, the expression’s value is null.

#### true

One of the two values that a boolean expression can possibly have.

The keywords and literal words are all called _reserved_ words because each of these words is reserved for special use in the Java programming language.

Restricted keywords
-------------------

With the release of Java 9, the language has ten new words called _restricted keywords_. A restricted keyword has a specific meaning in the language, but only if you use that word in a specific way. For example, if you write

`requires other.stuff;  
`  
you tell Java that your program won’t run unless it has access to some other code (the code contained in `other.stuff`). But if you write

`int requires = 10;  
`  
then `requires` is an ordinary `int` variable.

The following table lists Java’s restricted keywords.

**Restricted Keyword**

**What It Does**

exports

Indicates that the code in a particular package is available for use by code in other modules.

module

A bunch of packages.

open

Indicates that all the packages in a module are, in a certain way, available for use by code in other modules.

opens

Gets access to all the code in another module. This access uses Java reflection (which tends to be messy).

provides

Indicates that a module makes a service available.

requires

Indicates that the program won’t run unless it has access to the some other code.

to

Names the code that has permission to use a particular piece of code.

transitive

When my code requires use of the A code, and the Z code requires use of my code, the word transitive means that Z code automatically requires A code.

uses

Indicates that a module uses a service.

with

Specifies a particular way of using a service.

Identifiers in the Java API
---------------------------

The Java API (Application Programming Interface) has thousands of identifiers. Each identifier is the name of something (a class, an object, a method, or something like that). These identifiers include System, out, println, String, toString, JFrame, File, Scanner, next, nextInt, Exception, close, ArrayList, stream, JTextField, Math, Random, MenuItem, Month, parseInt, Query, Rectangle, Color, Oval, paint, Robot, SQLData, Stack, Queue, TimeZone, URL, and so many others.

You can reuse any of these names for any purpose in your code. But if you do, you might have trouble using a name with its normal meaning from the Java API. For example, you can write

`int System = 7;`

`java.lang.System.out.println(System);  
`  
But you can’t write

`int System = 7;`

`System.out.println(System);`

Identifiers that you (the programmer) declare
---------------------------------------------

In your own Java program, you can make up names to your heart’s delight. For example, in the code

`double multiplyByTwo(double myValue) {  
`  
`return myValue * 2;  
`  
`}`

the names `multiplyByTwo` and `myValue` are your very own identifiers.

When you create a new name, you can use letters, digits, underscores (\_), and dollar signs ($). But don’t start the name with a digit. If you try to start a name with a digit, Java replies with a “Please don’t do that” message.

#### About the Book Author

**Barry Burd, PhD,** is a computer science professor at Drew University. The author of _Java Programming for Android Developers For Dummies, Beginning Programming with Java For Dummies,_ and _Android Application Development All-in-One For Dummies,_ Barry also writes for _Server Side_ (theserverside.com), _Android Authority_ (androidauthority.com), _InfoQ.com_ and numerous other online publications.

2.  [Programming](https://www.dummies.com/programming/)
3.  [Java](https://www.dummies.com/programming/java/)
4.  Java All-in-One For Dummies Cheat Sheet

By [Doug Lowe](https://www.dummies.com/?s=&a=doug-lowe)

Writing Java statements (like `for` and `if`) and classes (like `Math` and `NumberFormat`) help you start and build strong programs. Variables hold different kinds of [Java data types](https://www.dummies.com/programming/java/the-eight-data-types-of-java/): numbers, characters, and true/false numbers. You designate Java operations that can be performed on operands, including arithmetic operators, relational operators (or binary) and logical operators (or Boolean).

![Java concept image](https://www.dummies.com/wp-content/uploads/Java-concept.jpg)

© DeymosHR/Shutterstock.com

Common Java Statements
----------------------

Java statements build programs. Every Java class must have a body, which is made up of one or more statements. You can write different kinds of statements, including declaration and expression.

### The _break_ statement

break;

### The _continue_ statement

continue;

### The _do_ statement

do
    {_statements_...}
while (_expression_);

### The _for_ statement

for (_init_; _test_; count)
    {_statements_...}

### The enhanced _for_ statement

for (type variable : array-or-
    collection)
    {statements...}

### The _if_ statement

if (_expression_)
    {_statements_...}
else
    {_statements_...}

### The _throw_ statement

throw (_exception_)

### The _switch_ statement

_switch (expression)_
{
    case _constant_:
        _statements_;
        break;
    default:
        _statements_;
        break;  
}

### The _while_ statement

while (_expression_)
    {_statements_...}

### The _try_ statement

try
    {_statements_...}
catch (_exception__\-class_ e)
    {_statements_...}...
finally
    {_statements_...}
try
    {_statements_...}
finally
    {_statements_...}

Primitive Data Types
--------------------

_Java data types_ are the kind of data you can store in a variable. _Primitive data types_ are defined by the language itself. Java defines a total of eight primitive types. Of the eight primitive data types, six are for numbers, one is for characters, and one is for true/false values. Of the six number types, four are types of integers, and two are types of floating-point numbers.

Type

Wrapper Class

Parse Method of Wrapper Class

`int`

`Integer`

`int parseInt(String s)`

`short`

`Short`

`short parseShort(String s)`

`long`

`Long<`/span>

`long parseLong(String s)`

`byte`

`Byte`

`byte parseByte(String s)`

`float`

`Float`

`float parseFloat(String s)`

`double`

`Double`

`double parseDouble(String s)`

`char`

`Character`

(none)

`boolean`

`Boolean`

`boolean parseBoolean(String s)`

Math and NumberFormat Classes
-----------------------------

Java classes lay the foundation for your programs. The Java `Math` and `NumberFormat` classes let you program number values, as well as format numbers and currencies.

**The _Math_ Class**

Method

Description

`num abs(num y);`

Absolute value of _y_ (num can be any numeric data type)

`num max(num y, num z);`

Maximum of _y_ and _z_

`num min(num y, num z);`

Minimum of _y_ and _z_

`double = Math. random();`

Random number, such that 0.0 < _x_ <= 1.0

**The _NumberFormat_ Class**

Method

Description

`NumberFormat  
getNumberInstance();`

Gets an instance that formats numbers.

`NumberFormat`

Gets an instance that formats currency.

`String format(x);`

Formats the specified number.

Java Operators
--------------

An _operator_ designates a mathematical operation or some other type of operation that can be performed on _operands._ Java has _arithmetic operators, relational operators_ (also known as _binary operators_) and _logical operators_ (also known as _B__oolean_ _operators)_.

**Arithmetic**

Operator

Description

+

Addition

–

Subtraction

\*

Multiplication

/

Division

%

Remainder

++

Increment

—

Decrement

+=

Addition and assignment

\-=

Subtraction and assignment

\*=

Multiplication and assignment

/=

Division and assignment

%=

Remainder and assignment

**Relational**

Operator

Description

\==

Equal

!=

Not equal

<

Less than

<=

Less than or equal to

\>

Greater than

\>=

Greater than or equal to

**Logical**

Operator

Description

!

Not

&

And

&&

Conditional and

|

Or

||

Conditional or

^

xor