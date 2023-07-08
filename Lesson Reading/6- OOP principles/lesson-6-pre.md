# Inheritance

## derive types to create more specialized behavior

Inheritance, together with encapsulation and polymorphism, is one of the three primary characteristics of object-oriented programming. Inheritance enables you to create new classes that reuse, extend, and modify the behavior defined in other classes. The class whose members are inherited is called the base class, and the class that inherits those members is called the derived class.

## Abstract and virtual methods

When a base class declares a method as virtual, a derived class can override the method with its own implementation. If a base class declares a member as abstract, that method must be overridden in any non-abstract class that directly inherits from that class. If a derived class is itself abstract, it inherits abstract members without implementing them. Abstract and virtual members are the basis for polymorphism, which is the second primary characteristic of object-oriented programming

## Abstract base classes

You can declare a class as abstract if you want to prevent direct instantiation by using the new operator. An abstract class can be used only if a new class is derived from it. An abstract class can contain one or more method signatures that themselves are declared as abstract.

## Interfaces

An interface is a reference type that defines a set of members. All classes and structs that implement that interface must implement that set of members. An interface may define a default implementation for any or all of these members. A class can implement multiple interfaces even though it can derive from only a single direct base class.

Interfaces are used to define specific capabilities for classes that don't necessarily have an "is a" relationship.

## Preventing further derivation

A class can prevent other classes from inheriting from it, or from any of its members, by declaring itself or the member as sealed.

## Derived class hiding of base class members

A derived class can hide base class members by declaring members with the same name and signature. The new modifier can be used to explicitly indicate that the member isn't intended to be an override of the base member.

## Abstract Classes and Class Members

Classes can be declared as abstract by putting the keyword abstract before the class definition.

An abstract class cannot be instantiated. The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.

Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.

If a virtual method is declared abstract, it is still virtual to any class inheriting from the abstract class. A class inheriting an abstract method cannot access the original implementation of the method

## Sealed Classes and Class Members

Classes can be declared as sealed by putting the keyword sealed before the class definition.

A sealed class cannot be used as a base class. For this reason, it cannot also be an abstract class. Sealed classes prevent derivation. Because they can never be used as a base class

## Polymorphism

Polymorphism is often referred to as the third pillar of object-oriented programming, after encapsulation and inheritance. Polymorphism is a Greek word that means "many-shaped" and it has two distinct aspects:

- At run time, objects of a derived class may be treated as objects of a base class in places such as method parameters and collections or arrays. When this polymorphism occurs, the object's declared type is no longer identical to its run-time type.

- Base classes may define and implement virtual methods, and derived classes can override them, which means they provide their own definition and implementation. At run-time, when client code calls the method, the CLR looks up the run-time type of the object, and invokes that override of the virtual method.

Virtual methods enable you to work with groups of related objects in a uniform way.

## Polymorphism overview

### Virtual members

When a derived class inherits from a base class, it includes all the members of the base class. All the behavior declared in the base class is part of the derived class. That enables objects of the derived class to be treated as objects of the base class.

Virtual methods gives the designer different choices for the behavior of the derived class:

- The derived class may override virtual members in the base class, defining new behavior.
- The derived class may inherit the closest base class method without overriding it, preserving the existing behavior but enabling further derived classes to override the method.
- The derived class may define new non-virtual implementation of those members that hide the base class implementations.

A derived class can override a base class member only if the base class member is declared as virtual or abstract. The derived member must use the override keyword to explicitly indicate that the method is intended to participate in virtual invocation.

### Hide base class members with new members

If you want your derived class to have a member with the same name as a member in a base class, you can use the new keyword to hide the base class member. The new keyword is put before the return type of a class member that is being replaced.

### Prevent derived classes from overriding virtual members

Virtual members remain virtual, regardless of how many classes have been declared between the virtual member and the class that originally declared it.

### Access base class virtual members from derived classes

A derived class that has replaced or overridden a method or property can still access the method or property on the base class using the base keyword.

## Object-Oriented programming (C#)

C# is an object-oriented programming language. The four basic principles of object-oriented programming are:

- Abstraction Modeling the relevant attributes and interactions of entities as classes to define an abstract representation of a system.
- Encapsulation Hiding the internal state and functionality of an object and only allowing access through a public set of functions.
- Inheritance Ability to create new abstractions based on existing abstractions.
- Polymorphism Ability to implement inherited properties or methods in different ways across multiple abstractions.
