# CLASSES AND OBJECTS

class defines a type of object but isnt object itself
object is concrete entity based on a class

classes declared using class keyword followed by unique identifier
obj created using the new keyword followed by name of the class

a class has a default value of null unless 

object is an instance of a class

if i dont create constructor a default one will be called

we can create a parametarized constructor which takes data from the user and define the new object with passed values as initial values

access modifiers:

public: The type or member can be accessed by any other code in the same assembly or another assembly that references it.
private: The type or member can be accessed only by code in the same class or struct.
protected: The type or member can be accessed only by code in the same class, or in a class that is derived from that class.
internal: The type or member can be accessed by any code in the same assembly, but not from another assembly

an assembly is a collection of types and resources that are built to work together and form a logical unit of functionality. Assemblies take the form of executable (.exe) or dynamic link library (.dll) files, and are the building blocks of .NET applications. All types in the .NET Framework must exist in assemblies; the common language runtime does not support types outside of assemblies.

properties are members that provide a flexible mechanism to read, write, or compute the values of private fields. Properties can be used as if they are public data members, but they are actually special methods called accessors

A property has two accessors: a get property accessor or a getter and a set property accessor or a setter. A get accessor returns a property value, and a set accessor assigns a new value. The value keyword represents the value of a property.

*lookup object initializer*

*look deeper into stack and heap*

