# Lesson 4

## Classes

A type that is defined as a class is a reference type. At run time, when you declare a variable of a reference type, the variable contains the value null until you explicitly create an instance of the class by using the new operator, or assign it an object of a compatible type that may have been created elsewhere

Classes are declared by using the class keyword followed by a unique identifier

### Creating objects

a class and an object are different things. A class defines a type of object, but it isn't an object itself. An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.

Objects can be created by using the new keyword followed by the name of the class

### Constructors and initialization

Whenever an instance of a class or a struct is created, its constructor is called. A class or struct may have multiple constructors that take different arguments. Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.

There are several actions that are part of initializing a new instance. Those actions take place in the following order:

1. Instance fields are set to 0. This is typically done by the runtime.
2. Field initializers run. The field initializers in the most derived type run.
3. Base type field initializers run. Field initializers starting with the direct base through each base type to System.Object.
4. Base instance constructors run. Any instance constructors, starting with Object.Object through each base class to the direct base class.
5. The instance constructor runs. The instance constructor for the type runs.
6. Object initializers run. If the expression includes any object initializers, those run after the instance constructor runs. Object initializers run in the textual order.

### Constructor syntax

A constructor is a method whose name is the same as the name of its type. Its method signature includes only an optional access modifier, the method name and its parameter list; it does not include a return type.

### Static constructors

A class or struct can also have a static constructor, which initializes static members of the type. Static constructors are parameterless. If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value

### Class inheritance

Classes fully support inheritance, a fundamental characteristic of object-oriented programming. When you create a class, you can inherit from any other class that isn't defined as sealed. Other classes can inherit from your class and override class virtual methods. Furthermore, you can implement one or more interfaces.

Inheritance is accomplished by using a derivation, which means a class is declared by using a base class from which it inherits data and behavior. A base class is specified by appending a colon and the name of the base class following the derived class name

## Properties overview

- Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.
- A get property accessor is used to return the property value, and a set property accessor is used to assign a new value.
- The value keyword is used to define the value being assigned by the set or init accessor.
- Properties can be read-write (they have both a get and a set accessor), read-only (they have a get accessor but no set accessor), or write-only (they have a set accessor, but no get accessor). Write-only properties are rare and are most commonly used to restrict access to sensitive data.
- Simple properties that require no custom accessor code can be implemented either as expression body definitions or as auto-implemented properties.

### Properties with backing fields

One basic pattern for implementing a property involves using a private backing field for setting and retrieving the property value. The get accessor returns the value of the private field, and the set accessor may perform some data validation before assigning a value to the private field. Both accessors may also perform some conversion or computation on the data before it's stored or returned.

### Expression body definitions

Property accessors often consist of single-line statements that just assign or return the result of an expression. You can implement these properties as expression-bodied members. Expression body definitions consist of the => symbol followed by the expression to assign to or retrieve from the property.

### Auto-implemented properties

In some cases, property get and set accessors just assign a value to or retrieve a value from a backing field without including any extra logic.

If a property has both a get and a set (or a get and an init) accessor, both must be auto-implemented. You define an auto-implemented property by using the get and set keywords without providing any implementation

### Required properties

you can add the required member to force client code to initialize any property or field

## Fundamentals of garbage collection

### Benefits

The garbage collector provides the following benefits:

- Frees developers from having to manually release memory.

- Allocates objects on the managed heap efficiently.

- Reclaims objects that are no longer being used, clears their memory, and keeps the memory available for future allocations. Managed objects automatically get clean content to start with, so their constructors don't have to initialize every data field.

- Provides memory safety by making sure that an object can't use for itself the memory allocated for another object.

### Fundamentals of memory

The following list summarizes important CLR memory concepts:

Each process has its own, separate virtual address space. All processes on the same computer share the same physical memory and the page file, if there's one.

By default, on 32-bit computers, each process has a 2-GB user-mode virtual address space.

As an application developer, you work only with virtual address space and never manipulate physical memory directly. The garbage collector allocates and frees virtual memory for you on the managed heap.

If you're writing native code, you use Windows functions to work with the virtual address space. These functions allocate and free virtual memory for you on native heaps.

Virtual memory can be in three states:

|State|Description|
| --- | --- |
|Free|The block of memory has no references to it and is available for allocation.|
|Reserved|The block of memory is available for your use and can't be used for any other allocation request. However, you can't store data to this memory block until it's committed.|
|Committed|The block of memory is assigned to physical storage.|

Virtual address space can get fragmented, which means that there are free blocks known as holes in the address space. When a virtual memory allocation is requested, the virtual memory manager has to find a single free block that is large enough to satisfy the allocation request.

You can run out of memory if there isn't enough virtual address space to reserve or physical space to commit.

The page file is used even if physical memory pressure (demand for physical memory) is low. The first time that physical memory pressure is high, the operating system must make room in physical memory to store data, and it backs up some of the data that's in physical memory to the page file.

### Memory allocation

When you initialize a new process, the runtime reserves a contiguous region of address space for the process. This reserved address space is called the managed heap. The managed heap maintains a pointer to the address where the next object in the heap will be allocated.

app makes first reference type. memory allocation is at base address of managed heap. next object allocated is immedietly following first object

Allocating memory from the managed heap is faster than unmanaged memory allocation. Because the runtime allocates memory for an object by adding a value to a pointer

<!-- ### Memory release i will stop here its getting late and i cant see straight any more-->
