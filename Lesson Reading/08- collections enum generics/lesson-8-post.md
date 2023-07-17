# ENUM

An enum is a value type defined by a set of named constants of the underlying integral numeric type in C#

    enum Season { Spring, Summer, Autumn, Winter }

By default, the associated constant values of enum members are of type int

## COLLECTIONS

In C#, collections are used to work with groups of objects. Unlike arrays, collections can grow and shrink dynamically as the needs of the application change

There are two main types of collections: generic collections and non-generic collections. Generic collections are type-safe at compile time and typically offer better performance

Non-generic collections store items as Object, require casting

## GENERICS

Generics in C# introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared

## BOXING AND UNBOXING

Boxing is the process of converting a value type to the type object or to any interface type implemented by this value type. When the common language runtime (CLR) boxes a value type, it wraps the value inside a System.Object instance and stores it on the managed heap. Unboxing extracts the value type from the object

## LISTS

The List < T > class is a collection of strongly typed objects that can be accessed by index. It provides methods to search, sort, and manipulate lists

## DICTIONARY

The Dictionary<TKey, TValue> class is a generic collection that stores key-value pairs in no particular order.

Keys must be unique and cannot be null, while values can be null or duplicate. Values can be accessed by passing the associated key in the indexer
