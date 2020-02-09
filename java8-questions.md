## Java 8 Interview Questions and Answers



#### Q. What are the important features of Java 8 release?
* Interface methods by default;
* Lambda expressions;
* Functional interfaces;
* References to methods and constructors;
* Repeatable annotations
* Annotations on data types;
* Reflection for method parameters;
* Stream API for working with collections;
* Parallel sorting of arrays;
* New API for working with dates and times;
* New JavaScript Nashorn Engine ;
* Added several new classes for thread safe operation;
* Added a new API for `Calendar`and `Locale`;
* Added support for Unicode 6.2.0 ;
* Added a standard class for working with Base64 ;
* Added support for unsigned arithmetic;
* Improved constructor `java.lang.String(byte[], *)` and method performance `java.lang.String.getBytes()`;
* A new implementation `AccessController.doPrivileged` that allows you to set a subset of privileges without having to check all * other access levels;
* Password-based algorithms have become more robust;
* Added support for SSL / TLS Server Name Indication (NSI) in JSSE Server ;
* Improved keystore (KeyStore);
* Added SHA-224 algorithm;
* Removed JDBC Bridge - ODBC;
* PermGen is removed , the method for storing meta-data of classes is changed;
* Ability to create profiles for the Java SE platform, which include not the entire platform, but some part of it;
* Tools
    * Added utility `jjs` for using JavaScript Nashorn;
    * The command `java` can run JavaFX applications;
    * Added utility `jdeps` for analyzing .class files.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

#### Q. Can you declare an interface method static?
Java 8 interface changes include static methods and default methods in interfaces. Prior to Java 8, we could have only method declarations in the interfaces. But from Java 8, we can have default methods and static methods in the interfaces.

#### Q. What is a lambda? What is the structure and features of using a lambda expression?
A lambda is a set of instructions that can be separated into a separate variable and then repeatedly called in various places of the program.

The basis of the lambda expression is the _lambda operator_ , which represents the arrow `->`. This operator divides the lambda expression into two parts: the left side contains a list of expression parameters, and the right actually represents the body of the lambda expression, where all actions are performed.

The lambda expression is not executed by itself, but forms the implementation of the method defined in the functional interface. It is important that the functional interface should contain only one single method without implementation.
```java
interface  Operationable {
     int  calculate ( int  x , int  y );
}

public  static  void main ( String [] args) {
    Operationable operation = (x, y) - > x + y;     
    int result = operation.calculate ( 10 , 20 );
    System.out.println (result); // 30 
}
```
In fact, lambda expressions are in some way a shorthand form of internal anonymous classes that were previously used in Java.

* _Deferred execution lambda expressions_ - it is defined once in one place of the program, it is called if necessary, any number of times and in any place of the program.

* _The parameters of the lambda expression_ must correspond in type to the parameters of the functional interface method:
```javascript
operation = ( int x, int y) - > x + y;
// When writing the lambda expression itself, the parameter type is allowed not to be specified: 
(x, y) - > x + y;
// If the method does not accept any parameters, then empty brackets are written, for example: 
() - >  30  +  20 ;
// If the method accepts only one parameter, then the brackets can be omitted: 
n - > n * n;
```
* Trailing lambda expressions are not required to return any value.
```java
interface  Printable {
     void  print( String  s );
}
 
public  static  void main ( String [] args) {
    Printable printer = s - >  System.out.println(s);
    printer.print("Hello, world");
}

// _ Block lambda - expressions_ are surrounded by curly braces . The modular lambda - expressions can be used inside nested blocks, loops, `design the if ` ` switch statement ', create variables, and so on . d . If you block a lambda - expression must return a value, it explicitly applies `statement return statement ' :


Operationable operation = ( int x, int y) - > {       
    if (y ==  0 ) {
        return  0 ;
    }
    else {
        return x / y;
    }
};
```
* Passing a lambda expression as a method parameter
```java
interface  Condition {
     boolean  isAppropriate ( int  n );
}

private  static  int sum ( int [] numbers, Condition condition) {
     int result =  0 ;
    for ( int i : numbers) {
         if (condition.isAppropriate(i)) {
            result + = i;
        }
    }
    return result;
}

public  static  void main ( String [] args) {
     System.out.println(sum ( new  int [] { 0 , 1 , 0 , 3 , 0 , 5 , 0 , 7 , 0 , 9 }, (n) - > n ! =  0 ));
} 
```
#### Q. What variables do lambda expressions have access to?
Access to external scope variables from a lambda expression is very similar to access from anonymous objects. 

* immutable ( effectively final - not necessarily marked as final) local variables;
* class fields
* static variables.

The default methods of the implemented functional interface are not allowed to be accessed inside the lambda expression.

#### Q. How to sort a list of strings using a lambda expression?
```java
public  static  List < String > sort ( List < String > list) {
    Collections.sort(list, (a, b) -> a.compareTo(b));
    return list;
}
```
#### Q. What is a method reference?
If the method existing in the class already does everything that is necessary, then you can use the method reference mechanism (method reference) to directly pass this method. The result will be exactly the same as in the case of defining a lambda expression that calls this method.
```java
private  interface  Measurable {
    public  int  length ( String  string );
}

public  static  void main ( String [] args) {
    Measurable a =  String::length;
    System.out.println(a.length("abc"));
}
```
Method references are potentially more efficient than using lambda expressions. In addition, they provide the compiler with better information about the type, and if you can choose between using a reference to an existing method and using a lambda expression, you should always use a method reference.

#### Q. What types of method references do you know?
* on the static method;
* per instance method;
* to the constructor.

#### Q. Explain the expression `System.out::println`
The specified expression illustrates passing a reference to a static method of a `println()`class `System.out`.

#### Q. What is a Functional Interface? What is SAM Interface?
#### Q. When do we go for Java 8 Stream API? Why do we need to use Java 8 Stream API in our projects?
#### Q. Explain Differences between Collection API and Stream API?
#### Q. What is Spliterator in Java SE 8? Differences between Iterator and Spliterator in Java SE 8?
#### Q. What is Optional in Java 8? What is the use of Optional?
#### Q. What is Type Inference? Is Type Inference available in older versions like Java 7 and Before 7 or it is available only in Java SE 8?
#### Q. What is differences between Functional Programming and Object-Oriented Programming?