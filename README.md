# Data Structures and Algorithms 1: ArrayLists, LinkedLists, Stacks and Queues
## Course GTx CS1332xl on edx.org 
## Notes taken by Xenon Santillan

Recommended text book: Data Structures and Algorithms in Java, 6th Edition by Michael H. Goldwasser, Michael T. Goodrich, and Roberto Tamassia
-----
## Introduction: Constructors, Generics, References, Iterator/Iterable, Comparator/Comparable, Big-O

Two types of equality checking: value equality and reference equality.

Value Equality is done through the '==' operator. The primary use will be to check if an object is 'null'.

Reference Equality is done through the .equals() method inherited from the Object class. This is to defer the '==' operator, unless the user overrides the .equals() method.

-----
## Primitive Data Types: int, long, double, char, etc.

Primitive types are not under the Object class, these types do not inherit the .equals() method. You must use the '==' operator to check for equality.

Example used in module:
```
int one1 = 1;
int one2 = 1;
int two1 = 2;
int two2 = 2;

one1 == one2; // => true
two1 == two2; // => true
one1 == two1; // => false
one1 == 1;    // => true
two1 == 2;    // => true
```

-----
# String Literals

The specific process (in Java) of creating a String is actually creating something called a String literal. Instead of creating new objects every time a String is created, it just creates literals/constants that are stored in a String pool for faster access. 
// String typing extends Object

The other way to create a String is similar to any other Object, using the 'new' keyword. This causes the String to act like an Object in terms of value/reference equality.

Example used in module:
```
String literal = "This is a string.";
String object = new String("This is a string.");
String unequal = "Nope.";

// Using == On Value Equal Strings
literal == object;                           // => false
literal == "This is a string.";              // => true
"This is a string." == "This is a string.";  // => true
object == "This is a string.";               // => false
object == new String("This is a string.");   // => false

// Using .equals() On Value Equal Strings
literal.equals(object);                      // => true
object.equals(literal);                      // => true
literal.equals("This is a string.");         // => true
object.equals("This is a string.");          // => true
"This is a string.".equals("This is a string.");               // => true
"This is a string.".equals(new String("This is a string."));   // => true

// Using == and .equals() on Unequal Strings
literal == unequal;          // => false
object == unequal;           // => false
literal.equals(unequal);     // => false
object.equals(unequal);      // => false
```