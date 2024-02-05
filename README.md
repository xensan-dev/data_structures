# Data Structures and Algorithms 1: ArrayLists, LinkedLists, Stacks and Queues

### Course GTx CS1332xl on edx.org 
### Notes taken by Xenon Santillan

### Recommended text book: Data Structures and Algorithms in Java, 6th Edition by Michael H. Goldwasser, Michael T. Goodrich, and Roberto Tamassia
--------------------------------------------------------
### Introduction: Constructors, Generics, References, Iterator/Iterable, Comparator/Comparable, Big-O

Two types of equality checking: value equality and reference equality.

Value Equality is done through the '==' operator. The primary use will be to check if an object is 'null'.

Reference Equality is done through the .equals() method inherited from the Object class. This is to defer the '==' operator, unless the user overrides the .equals() method.

----------------------------------------------------------------
### Primitive Data Types: int, long, double, char, etc.

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

----------------------------------------------------------------
### String Literals

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
----------------------------------------------------------------
### Null Checking

The primary use of '==' will be to check if an Object is null. This is usually to check the validity of an input, or to check for an exception. If you try to invoke a null object, you will get a NullPointerException or NPE for short.

Example from module:
```String nullObject = null;
String normalObject = "normal";

// The correct way of checking if an object is null
nullObject == null;   // => true
normalObject == null; // => false

// The String class checks if argument is null, so it will throw NPE.  
// If a .equals() method doesn't check for a null argument, it will crash and throw a NPE.
// Here, we are comparing the value stored in normalObject to the values null, and nullObject
normalObject.equals(null);       // => false
normalObject.equals(nullObject); // => false

// However, here we invoking the .equals() method on a null object stored in nullOject
// This will cause a NPE to be thrown, regardless of the parameter in the .equals() method
nullObject.equals(normalObject);  // causes NullPointerException
nullObject.equals(null);          // causes NullPointerException
```
---------------
### Wrapper Objects

Each of the primitive types have a wrapper object class. There are moments where objects are needed in place of primitive types. An example would be generic typings, where it requires the data type to inherit from the object class. 
// to create a 'collection' of 'int's, you would need to make 'Integer' objects to add into the collection rather than primitives.

Example from module:
```
Integer primitive = 1;
Integer object = new Integer(1);
Integer unequal = 2;

// Using == On Value Equal Integers
primitive == object;        // => false
primitive == 1;             // => true
object == 1;                // => true
object == new Integer(1);   // => false

// Using .equals() On Value Equal Integers
primitive.equals(object);                 // => true
object.equals(primitive);                 // => true
primitive.equals(1);                      // => true
object.equals(1);                         // => true
(new Integer(1)).equals(1);               // => true
(new Integer(1)).equals(new Integer(1));  // => true

// Using == and .equals() on Unequal Integers
primitive == unequal;        // => false
object == unequal;           // => false
primitive.equals(unequal);   // => false
object.equals(unequal);      // => false

// If run, the following do not work since 1 is considered a primitive without autoboxing
1.equals(primitive);  // causes Error
1.equals(1);          // causes Error
```
-------
### Pass by value/reference

- Pass By Value - The helper method takes in the value of what was passed in. Changing its value will change the value of the local variable, but not the value of the original variable (because they reference two different locations in memory).

- Pass By Reference - The helper method takes in the reference for what was passed in. Changing its value will change the value of both the local variable and the original variable (because they reference the same location in memory).


