# OOP

## Encapsulation

 is a way to hide the details of a class and only show what’s necessary.

It can be done by making variables private and using properties to access them.

## Inheritance

we implement inheritance as such (public class car : vehicle{})

Inheritance lets one class take on the properties and methods of another class. The class that is inherited from is called the base class and the class that inherits is called the derived class.

## Access modifiers

- public: Members declared as public are accessible from any code in the program.
- private: Members declared as private are only accessible within the same class in which they are declared.
- protected: Members declared as protected are accessible within the same class and any derived classes.

## Overloading

overloading refers to the ability to have multiple methods with the same name but with different parameters. This is known as method overloading.

operator overloading, which is a way to define a custom implementation of an operation in case one or both of the operands are of a user-defined type.

properties in C# cannot be overloaded.

adding virtual keyword to the method in the base class enables overriding (public virtual void ...)

adding override to the method that is going to override the base class (public override void ...)

## Base

The base keyword in C# is used to access members of the base class from within a derived class. It can be used to call the base class constructor or to access base class methods and properties that have been overridden or hidden by the derived class.

## Polymorphism

Allows the objects of different classes to be treated as instances of the same class. This means that you can write code that works with objects of the base class or interface, and it will also work with objects of any derived class.

the ability of a single function or method to operate on multiple types of data. In C#, polymorphism is achieved through the use of inheritance and interfaces.

two types of polymorphism in C# : Compile-time polymorphism is achieved through method overloading, where multiple methods can have the same name but different parameters. Run-time polymorphism is achieved through method overriding, where a derived class can override a method from its base class.

*lookup List implementation in C#*

## Abstraction

refers to the process of exposing only the necessary and essential details of an object while hiding the inner workings and complexities.

An abstract class is a class that cannot be instantiated and is meant to be inherited by other classes.

to define abstract members use abstract keyword (public absteact void ...)
