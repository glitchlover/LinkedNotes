
# Page: 67
type: text-highlight
created: 2020-06-04T06:44:01.068Z
color: yellow
When you design a class, think about the objects that 
will be cre ated f rom that class t ype. Think about:

things the object 
knows

things the object 
does

type: area-highlight
created: 2020-06-04T06:44:31.126Z
color: yellow
![[screenshot.1.png]]

 # Page: 69
type: text-highlight
created: 2020-06-04T06:47:24.777Z
color: #9900EF
Making your first object

# Page: 69
type: text-highlight
created: 2020-06-04T06:48:27.317Z
color: yellow
class Dog {
  int size;
  String breed;
  String name;
  void bark() {
    System.out.println(“Ruff! Ruff!”);
  }
}

# Page: 69
type: text-highlight
created: 2020-06-04T06:48:31.620Z
color: #9900EF
1
Write your class

# Page: 69
type: text-highlight
created: 2020-06-04T06:49:01.474Z
color: yellow
```java
class DogTestDrive {
   public static void main (String[] args) {
     // Dog test code goes  here
   }
}
```

# Page: 69
type: text-highlight
created: 2020-06-04T06:49:04.429Z
color: #9900EF
2
Write a tester (TestDrive) class

# Page: 69
type: text-highlight
created: 2020-06-04T06:51:28.229Z
color: #9900EF
3
In your tester, make an object and access 
the object’s variables and methods

# Page: 69
type: text-highlight
created: 2020-06-04T06:51:50.340Z
color: yellow
lass DogTestDrive {
   public static void main (String[] args) {
     Dog d = new Dog();
d
.
size = 40;
     d
.
bark();
   }
}

# Page: 71
type: text-highlight
created: 2020-06-04T06:53:43.146Z
color: #9900EF
Quick! Ge t out of main!

# Page: 71
type: text-highlight
created: 2020-06-04T06:53:51.381Z
color: yellow
.            56           >%&   

# Page: 71
type: text-highlight
created: 2020-06-04T06:54:04.087Z
color: yellow
    >>      
   %&  "         %&          56   
         %&

# Page: 71
type: text-highlight
created: 2020-06-04T06:54:17.490Z
color: #9900EF
The t wo use s of main:

# Page: 71
type: text-highlight
created: 2020-06-04T06:54:20.924Z
color: yellow

to 
test 
your real class

to 
launch/start
 your Java 
application

# Page: 71
type: text-highlight
created: 2020-06-04T06:55:05.961Z
color: yellow
.               %  %&  "         %&

type: area-highlight
created: 2020-06-04T07:07:43.587Z
color: 
image: file:///C:/Users/User/.polar/files/image/12Y5YrarPY2BTjfkrdKL.png

# Page: 43
type: text-highlight
created: 2020-06-04T07:08:50.518Z
color: red
What can you say in the main me thod?

# Page: 43
type: text-highlight
created: 2020-06-04T07:08:54.166Z
color: #9900EF
1
do some thing

# Page: 43
type: text-highlight
created: 2020-06-04T07:08:57.553Z
color: yellow
 H            
     
int x = 3;
String name = “Dirk”;
x = x * 17;
System.out.print(“x  is ” + x);
double d = Math.random();
// this is a comment

# Page: 43
type: text-highlight
created: 2020-06-04T07:09:05.320Z
color: #9900EF
2
do some thing again and again

# Page: 43
type: text-highlight
created: 2020-06-04T07:09:09.122Z
color: yellow
-  H#    
while (x  > 12) { 
   x = x -1;
}
for (int x = 0; x < 10; x = x + 1) {
   System.out.print(“x is now ” + x);
}

# Page: 43
type: text-highlight
created: 2020-06-04T07:09:13.776Z
color: #9900EF
3
do some thing under this condition

# Page: 43
type: text-highlight
created: 2020-06-04T07:09:19.769Z
color: yellow
     H #$    
if (x == 10) {
   System.out.print(“x must be 10”);
} else {
   System.out.print(“x isn’t 10”);
}
if ((x < 3) & (name.equals(“Dirk”))) {
   System.out.println(“Gently”);
}
System.out.print(“this line runs no matter what”);

# Page: 51
type: text-highlight
created: 2020-06-04T07:10:06.310Z
color: red
The compiler and 
the JVM battle over the question, 
“Who’s more important?”

# Page: 36
type: text-highlight
created: 2020-06-04T07:12:40.443Z
color: #9900EF
What you’ll do in Java

# Page: 86
type: text-highlight
created: 2020-06-18T06:26:03.742Z
color: #9900EF
Back away f rom that key word!

# Page: 86
type: text-highlight
created: 2020-06-18T06:26:33.686Z
color: yellow
It must start with a letter, underscore (_), or 
dollar sign ($). You can’t start a name with a 
number.

After the fi rst character, you can use numbers as 
well. Just don’t start it with a number.

  It can be anything you like, subject to those two 
rules, just so long as it isn’t one of Java’s reserved 
words. 

# Page: 87
type: text-highlight
created: 2020-06-18T06:30:15.821Z
color: #9900EF
Cont rolling your Dog object

# Page: 87
type: text-highlight
created: 2020-06-18T06:31:38.582Z
color: yellow
Think of a Dog 
reference variable as 
a Dog remote control. 
You use it to get the 
object to do something 
(invoke methods).

type: area-highlight
created: 2020-06-18T06:32:00.144Z
color: 
image: file:///C:/Users/User/.polar/files/image/12KKxxTEL576CvhcRLh6.png

# Page: 87
type: text-highlight
created: 2020-06-18T06:33:04.141Z
color: yellow
t doesn’t hold the object itself, but it holds something 
li
ke a pointer. Or an address.

# Page: 87
type: text-highlight
created: 2020-06-18T06:33:08.205Z
color: yellow
Except, in Java we don’t 
really know 
what
 is inside a reference variable.

# Page: 87
type: text-highlight
created: 2020-06-18T06:33:11.079Z
color: yellow
And the JVM knows how to use the reference to 
get to the object.

# Page: 88
type: text-highlight
created: 2020-06-18T06:34:34.010Z
color: #9900EF
An object reference is just     
another variable value. 

# Page: 88
type: text-highlight
created: 2020-06-18T06:34:42.293Z
color: yellow
            )
.     0             )

type: area-highlight
created: 2020-06-18T06:35:39.348Z
color: 
image: file:///C:/Users/User/.polar/files/image/1227aAadmdb3qC44PGE8.png

# Page: 88
type: text-highlight
created: 2020-06-18T06:36:15.587Z
color: yellow
Primiti ve Variable

type: area-highlight
created: 2020-06-18T06:36:24.156Z
color: 
image: file:///C:/Users/User/.polar/files/image/12Hc3Pmc3oxjpytvdaPJ.png

# Page: 88
type: text-highlight
created: 2020-06-18T06:36:48.939Z
color: yellow
Reference Variable

type: area-highlight
created: 2020-06-18T06:36:54.445Z
color: 
image: file:///C:/Users/User/.polar/files/image/19qu3xNGzqChCR6BuQVw.png

# Page: 88
type: text-highlight
created: 2020-06-18T06:37:59.918Z
color: yellow
Link the object 
and the reference

type: area-highlight
created: 2020-06-18T06:38:09.692Z
color: 
image: file:///C:/Users/User/.polar/files/image/12o17Wy8g5RwRKmncLFH.png

# Page: 90
type: text-highlight
created: 2020-06-18T06:41:55.439Z
color: #9900EF
Life on the garbage-collectible he ap

# Page: 91
type: text-highlight
created: 2020-06-18T06:47:52.180Z
color: yellow
Book b = new Book();
Book c = new Book();

type: area-highlight
created: 2020-06-18T06:48:10.137Z
color: 
image: file:///C:/Users/User/.polar/files/image/1mRZhjqJrL8NpfNVGFwz.png

# Page: 91
type: text-highlight
created: 2020-06-18T06:49:05.290Z
color: yellow
b = c;

# Page: 91
type: text-highlight
created: 2020-06-18T06:49:18.198Z
color: yellow
Both b and c refer to the same 
object.  Object 1 is abandoned 
and eligible for Garbage Collec-
tion (GC).

type: area-highlight
created: 2020-06-18T06:49:25.099Z
color: 
image: file:///C:/Users/User/.polar/files/image/1rFUocCckFtHnGnGo1Fy.png

# Page: 91
type: text-highlight
created: 2020-06-18T06:50:07.360Z
color: yellow
c = null;

# Page: 91
type: text-highlight
created: 2020-06-18T06:50:12.919Z
color: yellow
Object 2 still has an active 
reference (
b
), and as long 
as it does, the object is not 
eligible for GC

type: area-highlight
created: 2020-06-18T06:50:16.983Z
color: 
image: file:///C:/Users/User/.polar/files/image/12mXoVK9ziJ26Snpa6Ax.png

# Page: 92
type: text-highlight
created: 2020-06-18T06:51:28.829Z
color: yellow
Arrays are objects too 

# Page: 95
type: text-highlight
created: 2020-06-18T06:53:53.030Z
color: yellow
Variables come in two flavors: primitive and 
reference

# Page: 95
type: text-highlight
created: 2020-06-18T06:54:13.707Z
color: yellow
   A reference variable has a value of 
null
 when 
it is not referencing any object.

# Page: 107
type: text-highlight
created: 2020-06-22T12:33:50.007Z
color: #9900EF
You can send things to a me thod

# Page: 108
type: text-highlight
created: 2020-06-22T12:35:41.606Z
color: #9900EF
You can ge t things 
back
 f rom a me thod.

# Page: 109
type: text-highlight
created: 2020-06-22T12:36:32.311Z
color: #9900EF
You can send more than one thing 
to a me thod

# Page: 110
type: text-highlight
created: 2020-07-03T14:36:23.066Z
color: #9900EF
Java is pass-by-value.
That me ans pass-by-copy.

type: area-highlight
created: 2020-07-03T14:36:44.191Z
color: 
image: file:///C:/Users/User/.polar/files/image/1nxQ1irzJHmheBFZCq8M.png

type: area-highlight
created: 2020-07-03T14:37:36.126Z
color: 
image: file:///C:/Users/User/.polar/files/image/1YxHrfzmEeVrAm7tVdP8.png

# Page: 113
type: text-highlight
created: 2020-07-03T14:38:41.583Z
color: #9900EF
Encapsulation
Do it or risk humiliation and 
ridicule.

type: area-highlight
created: 2020-07-03T14:48:24.642Z
color: 
image: file:///C:/Users/User/.polar/files/image/12P7bhok39YdSso18cSp.png

type: area-highlight
created: 2020-07-03T14:52:13.320Z
color: 
image: file:///C:/Users/User/.polar/files/image/19HDDG2WL7QrJc73NywU.png

type: area-highlight
created: 2020-07-03T14:53:35.200Z
color: 
image: file:///C:/Users/User/.polar/files/image/12WfFPC87xTKJiMfXe8T.png

# Page: 116
type: text-highlight
created: 2020-07-03T14:59:12.673Z
color: #9900EF
How do objects in an array 
behave?

type: area-highlight
created: 2020-07-03T15:01:17.377Z
color: 
image: blob:http://localhost:8500/f6427b83-33b5-4449-aa19-b8d7e83c132c

type: area-highlight
created: 2020-07-03T15:11:54.275Z
color: 
image: file:///C:/Users/User/.polar/files/image/12Mo4ZrhfY5PWQnZWdvp.png

# Page: 117
type: text-highlight
created: 2020-07-03T15:12:43.698Z
color: yellow
Instance variables 
always get a 
default value. If 
you don’t explicitly 
assign a value 
to an instance 
variable, or you 
don’t call a setter 
method, the 
instance variable 
still has a value!
integers                      0
floating points  0.0
booleans                      false
references             null

# Page: 118
type: text-highlight
created: 2020-07-03T15:14:19.992Z
color: yellow
Local variables do 
NOT get a default 
value! The compiler 
complains if you 
try to use a local 
variable before 
the variable is 
initialized.

# Page: 128
type: text-highlight
created: 2020-07-03T15:17:17.571Z
color: #9900EF
Extra-Strength Methods

# Page: 107
type: comment
created: 2020-08-05T14:39:11.254Z
<p>using parameter and arguments</p><p><br></p>

# Page: 108
type: comment
created: 2020-08-05T14:39:27.064Z
<p>using return</p>

# Page: 109
type: comment
created: 2020-08-05T14:40:03.591Z
<p>using two or more parameter and arguments</p>

# Page: 110
type: comment
created: 2020-08-05T14:41:20.836Z
<p>Which means changing z value will not change x value at all</p>

# Page: 112
type: text-highlight
created: 2020-08-05T14:47:33.198Z
color: #9900EF
Cool things you can do with parame ters 
and re turn t ype s

# Page: 112
type: text-highlight
created: 2020-08-05T14:47:56.698Z
color: yellow

            E
/  
 
  

type: area-highlight
created: 2020-08-05T15:37:44.694Z
color: 
image: blob:http://localhost:8500/bcba4039-167c-402a-9881-ee85f76cb7e6

# Page: 117
type: text-highlight
created: 2020-08-05T15:39:04.561Z
color: #9900EF
Declaring and initializing 
instance variables

# Page: 118
type: text-highlight
created: 2020-08-05T15:40:49.622Z
color: #9900EF
The dif ference be t ween instance 
and local variable s

# Page: 119
type: text-highlight
created: 2020-08-05T15:42:17.991Z
color: #9900EF
Comparing variable s (primiti ve s or reference s)

# Page: 119
type: text-highlight
created: 2020-08-05T15:43:31.508Z
color: yellow
Use == to compare 
two primitives, 
or to see if two 
references refer to 
the 
same
 object. 
Use the equals() 
method to see 
if
 tw
o 
different 
objects are equal.

# Page: 158
type: text-highlight
created: 2020-08-05T15:48:47.123Z
color: #9900EF
Using the Java Library
