# Data Structures and Algorithms 1: ArrayLists, LinkedLists, Stacks and Queues
## Course GTx CS1332xl on edx.org 
## Notes taken by Xenon Santillan

-----
## Introduction: Constructors, Generics, References, Iterator/Iterable, Comparator/Comparable, Big-O

Two types of equality checking: value equality and reference equality.

Value Equality is done through the '==' operator. The primary use will be to check if an object is 'null'.

Reference Equality is done through the .equals() method inherited from the Object class. This is to defer the '==' operator, unless the user overrides the .equals() method.

-----
## Primitive Data Types: int, long, double, char, etc.

Primitive types are not under the Object class, these types do not inherit the .equals() method. You must use the '==' operator to check for equality.

Example:

int one1 = 1;
int one2 = 1;
int two1 = 2;
int two2 = 2;

one1 == one2; // => true
two1 == two2; // => true
one1 == two1; // => false
one1 == 1;    // => true
two1 == 2;    // => true

-----
# String Literals

This specific process of creating a String is actually creating something called a String literal. 