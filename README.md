# Comp-Sci-Notes-9-27-2021

## Abstract Classes and Interfaces

### UML access
* + Public
* - Private
* # Protected
* ~ Package (default visibility)
* underline = static
* *italic* abstract
* ALL-CAPS constants

### Classes as Contracts
* Recall: the public interface of a class is a promise to users of the class
  * Guarantee that certain methods will be available and that they have specific prototypes
* These Promises extend into the class hierarchy
  * The superclass makes certain promises about available methods and instance variables
  * These promises must be kept by all child classes
    * But: the implementation of the promises can be overwritten
* Sometimes, a superclass needs to make a promise, but cannot provide an implementation
  * Declare methods as abstract
### Abstract Classes
* Cannot be instantiated
 ```java
     Produce p = new Produce();
 ```
 ^Nope
 * ... but can be used as types
 ```java
    Produce p = new Apple();
 ```
 Very powerful
 A class that extends an abstract class must:
 * Implement the abstract method
 * Be declared abstract

### Properties of Abstract Classes
Must provide constructors
* These constructors are protected or private
* Child classes can reference these with super()
* Could be the default constructor

### Best Practices
Int the abstract superclass:
* Provide as many method implementations as possible
* These implementations may call abstract methods
  * The methods will ultimately be implemented by the child classes
  * It is these concrete classes that ensure all methods are implemented

### "Multiple" Inheritance
Example: we might want to make a superclass of Cloneable objects
* A clone of an object is equal in content but distinct in memory footprint
* Clone is not just a copy of the object's memory, but of all of its component objects
* Cloneable requires the implementation of a clone method that produces the copy

## But there is a problem...
Java restriction:
* If a class inherits from the Cloneable class, then it cannot inherit from any other class

### Java's Workaround: The Interface
* An interface defines no implementation - only a set of abstract methods
* All checks can be made at compile time, so the runtime cost is low
* It is a class-like construct

### How Does this Fix Our Cloneable Problem?
We can extend a different class and still make the same guarantees as those provided by Cloneable:
```java
public class Apple extends Fruit implements Cloneable
{
  :
  :
}
```
A class can implement any number of interfaces

### Comparable<T>
  This interface requires only one method
  `int compareTo(T object)`
* T is a placeholder for any class name
* Returns
  * negative number if this < object
  * zero if they are equal
  * positive number if this > object
* Defines a Natural Ordering of objects of class T
  * Basis for using generic sorting methods
  
 ### Example
* Person class
  * first name
  * last name
  * phone number
* Implement comparableTo sort by
  * last name then by first name
* Show use with Collections.sort()
 
