#Note-Java #need-revise #need-retouch 
linkes: [[Java Cheetsheet#instanceof]]


https://www.javatpoint.com/downcasting-with-instanceof-operator

> The Java instanceof operator is used to test if the object or instance is an instanceof the specified type (class or subclass or interface), how downcasting in java is possible with instanceof operator:

# Java instanceof - javatpoint

The **java instanceof operator** is used to test whether the object is an instance of the specified type (class or subclass or interface).

The instanceof in java is also known as type _comparison operator_ because it compares the instance with type. It returns either true or false. If we apply the instanceof operator with any variable that has null value, it returns false.

### Simple example of java instanceof

Let's see the simple example of instance operator where it tests the current class.

1.  class Simple1{ 
2.   public static void main(String args\[\]){ 
3.   Simple1 s=new Simple1(); 
4.   System.out.println(s instanceof Simple1); 
5.   } 
6.  } 

[Test it Now](https://www.javatpoint.com/opr/test.jsp?filename=Simple1)

***

An object of subclass type is also a type of parent class. For example, if Dog extends Animal then object of Dog can be referred by either Dog or Animal class.

Another example of java instanceof operator
-------------------------------------------

```java
1.  class Animal{} 
2.  class Dog1 extends Animal{ 

4.   public static void main(String args\[\]){ 
5.   Dog1 d=new Dog1(); 
6.   System.out.println(d instanceof Animal); 
7.   } 
8.  } 
```

[Test it Now](https://www.javatpoint.com/opr/test.jsp?filename=Dog1)

***

instanceof in java with a variable that have null value
---------------------------------------------------
If we apply instanceof operator with a variable that have null value, it returns false. Let's see the example given below where we apply instanceof operator with the variable that have null value.

```java
1.  class Dog2{ 
2.   public static void main(String args\[\]){ 
3.   Dog2 d=null; 
4.   System.out.println(d instanceof Dog2); 
5.   } 
6.  } 
```

[Test it Now](https://www.javatpoint.com/opr/test.jsp?filename=Dog2)

***

Downcasting with java instanceof operator
-----------------------------------------

When Subclass type refers to the object of Parent class, it is known as downcasting. If we perform it directly, compiler gives Compilation error. If you perform it by typecasting, ClassCastException is thrown at runtime. But if we use instanceof operator, downcasting is possible.

If we perform downcasting by typecasting, ClassCastException is thrown at runtime.

### Possibility of downcasting with instanceof

Let's see the example, where downcasting is possible by instanceof operator.

1.  class Animal { } 

3.  class Dog3 extends Animal { 
4.   static void method(Animal a) { 
5.   if(a instanceof Dog3){ 
6.   Dog3 d=(Dog3)a; 
7.   System.out.println("ok downcasting performed"); 
8.   } 
9.   } 

11.   public static void main (String \[\] args) { 
12.   Animal a=new Dog3(); 
13.   Dog3.method(a); 
14.   } 

16.   } 

[Test it Now](https://www.javatpoint.com/opr/test.jsp?filename=Dog3)

Output:ok downcasting performed

***

### Downcasting without the use of java instanceof

Downcasting can also be performed without the use of instanceof operator as displayed in the following example:

```java
1.  class Animal { } 
2.  class Dog4 extends Animal { 
3.   static void method(Animal a) { 
4.   Dog4 d=(Dog4)a; 
5.   System.out.println("ok downcasting performed"); 
6.   } 
7.   public static void main (String \[\] args) { 
8.   Animal a=new Dog4(); 
9.   Dog4.method(a); 
10.   } 
11.  } 
```
[Test it Now](https://www.javatpoint.com/opr/test.jsp?filename=Dog4)

Output:ok downcasting performed

Let's take closer look at this, actual object that is referred by a, is an object of Dog class. So if we downcast it, it is fine. But what will happen if we write:

1.  Animal a=new Animal(); 
2.  Dog.method(a); 

### Understanding Real use of instanceof in java

Let's see the real use of instanceof keyword by the example given below.

1.  interface Printable{} 
2.  class A implements Printable{ 
3.  public void a(){System.out.println("a method");} 
4.  } 
5.  class B implements Printable{ 
6.  public void b(){System.out.println("b method");} 
7.  } 

9.  class Call{ 
10.  void invoke(Printable p){ 
11.  if(p instanceof A){ 
12.  A a=(A)p; 
13.  a.a(); 
14.  } 
15.  if(p instanceof B){ 
16.  B b=(B)p; 
17.  b.b(); 
18.  } 

20.  } 
21.  } 

23.  class Test4{ 
24.  public static void main(String args\[\]){ 
25.  Printable p=new B(); 
26.  Call c=new Call(); 
27.  c.invoke(p); 
28.  } 
29.  } 

[Test it Now](https://www.javatpoint.com/opr/test.jsp?filename=Test4)
