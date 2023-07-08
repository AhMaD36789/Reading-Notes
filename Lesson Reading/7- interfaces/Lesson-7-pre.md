# Interfaces

An interface contains definitions for a group of related functionalities that a non-abstract class or a struct must implement. An interface may define static methods, which must have an implementation. An interface may define a default implementation for members. An interface may not declare instance data such as fields, auto-implemented properties, or property-like events.

By using interfaces, you can, for example, include behavior from multiple sources in a class. That capability is important in C# because the language doesn't support multiple inheritance of classes. In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.

The name of an interface must be a valid C# identifier name. By convention, interface names begin with a capital I.

Interfaces can contain instance methods, properties, events, indexers, or any combination of those four member types. Interfaces may contain static constructors, fields, constants, or operators.

A class or struct that implements an interface must provide an implementation for all declared members without a default implementation provided by the interface. However, if a base class implements an interface, any class that's derived from the base class inherits that implementation.

## Interfaces summary

- An interface may define default implementations for some or all of its members. A class or struct that implements the interface doesn't have to implement members that have default implementations. For more information, see default interface methods.
- An interface can't be instantiated directly. Its members are implemented by any class or struct that implements the interface.
- A class or struct can implement multiple interfaces. A class can inherit a base class and also implement one or more interfaces.

## What problem does the interface solve?

The basic problem an interface is trying to solve is to separate how we use something from how it is implemented. So that we can write code that can work with a variety of different implementations of some set of responsibilities without having to specifically handle each implementation.

Interfaces allow us to specify that a particular class meets certain expectations that other classes can rely on.

If we have a class that implements an interface, we can be sure that it will support all the methods that are defined in that interface.

At first glance interfaces seem to be similar to concrete inheritance, but there is a key difference.

Concrete inheritance says Car is an Automobile, while an interface says Car implements the Drivable interface.

When a class implements an interface, it does not mean that class IS that interface.  For this reason interfaces that completely describe the functionality of a class are usually wrong.

Interfaces are kind of a shortcut that allows us to get rid of having lots of dependencies in a class.

## Static abstract and virtual members

An interface may declare static abstract and static virtual members for all member types except fields. Interfaces can declare that implementing types must define operators or other static members. This feature enables generic algorithms to specify number-like behavior.

## Interface inheritance

Interfaces may not contain instance state. While static fields are now permitted, instance fields aren't permitted in interfaces. Instance auto-properties aren't supported in interfaces, as they would implicitly declare a hidden field

An interface can inherit from one or more base interfaces. When an interface overrides a method implemented in a base interface, it must use the explicit interface implementation syntax.


