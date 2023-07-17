# Collections & Enums

Collections provide a more flexible way to work with groups of objects. Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.

## Kinds of Collections

Many common collections are provided by .NET. Each type of collection is designed for a specific purpose.

Some of the common collection classes are described in this section:

- System.Collections.Generic classes

- System.Collections.Concurrent classes

- System.Collections classes

### System.Collections.Generic Classes

You can create a generic collection by using one of the classes in the System.Collections.Generic namespace. A generic collection is useful when every item in the collection has the same data type. A generic collection enforces strong typing by allowing only the desired data type to be added.

|class|description|
| --- | --- |
|Dictionary<TKey,TValue>|Represents a collection of key/value pairs that are organized based on the key.|
|List< T>|Represents a list of objects that can be accessed by index. Provides methods to search, sort, and modify lists.|
|Queue< T>|Represents a first in, first out (FIFO) collection of objects.|
|SortedList<TKey,TValue>|Represents a collection of key/value pairs that are sorted by key based on the associated IComparer< T> implementation.|
|Stack< T>|Represents a last in, first out (LIFO) collection of objects.|

### System.Collections.Concurrent Classes

the collections in the System.Collections.Concurrent namespace provide efficient thread-safe operations for accessing collection items from multiple threads.

The classes in the System.Collections.Concurrent namespace should be used instead of the corresponding types in the System.Collections.Generic and System.Collections namespaces whenever multiple threads are accessing the collection concurrently. For more information, see Thread-Safe Collections and System.Collections.Concurrent.

### System.Collections Classes

The classes in the System.Collections namespace do not store elements as specifically typed objects, but as objects of type Object.

Whenever possible, you should use the generic collections in the System.Collections.Generic namespace or the System.Collections.Concurrent namespace instead of the legacy types in the System.Collections namespace.

The following table lists some of the frequently used classes in the System.Collections namespace:

|Class|Description|
| --- | --- |
|ArrayList|Represents an array of objects whose size is dynamically increased as required.|
|Hashtable|Represents a collection of key/value pairs that are organized based on the hash code of the key.|
|Queue|Represents a first in, first out (FIFO) collection of objects.|
|Stack|Represents a last in, first out (LIFO) collection of objects.|

The System.Collections.Specialized namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.

## Implementing a Collection of Key/Value Pairs

The Dictionary<TKey,TValue> generic collection enables you to access to elements in a collection by using the key of each element. Each addition to the dictionary consists of a value and its associated key. Retrieving a value by using its key is fast because the Dictionary class is implemented as a hash table.

## Using LINQ to Access a Collection

LINQ (Language-Integrated Query) can be used to access collections. LINQ queries provide filtering, ordering, and grouping capabilities. For more information, see Getting Started with LINQ in C#.

## Defining a Custom Collection

You can define a collection by implementing the IEnumerable<T> or IEnumerable interface.

Although you can define a custom collection, it is usually better to instead use the collections that are included in .NET, which are described in Kinds of Collections earlier in this article.

The following example defines a custom collection class named AllColors. This class implements the IEnumerable interface, which requires that the GetEnumerator method be implemented.

## Iterators

An iterator is used to perform a custom iteration over a collection. An iterator can be a method or a get accessor. An iterator uses a yield return statement to return each element of the collection one at a time.

You call an iterator by using a foreach statement. Each iteration of the foreach loop calls the iterator. When a yield return statement is reached in the iterator, an expression is returned, and the current location in code is retained. Execution is restarted from that location the next time that the iterator is called.

## Enumeration types (C# reference)

An enumeration type (or enum type) is a value type defined by a set of named constants of the underlying integral numeric type. To define an enumeration type, use the enum keyword and specify the names of enum members

## Enumeration types as bit flags

If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field. That is, the associated values of those enum members should be the powers of two.

## The System.Enum type and enum constraint

The System.Enum type is the abstract base class of all enumeration types. It provides a number of methods to get information about an enumeration type and its values.

You can use System.Enum in a base class constraint (that is known as the enum constraint) to specify that a type parameter is an enumeration type. Any enumeration type also satisfies the struct constraint, which is used to specify that a type parameter is a non-nullable value type.

## Conversions

For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type. If you cast an enum value to its underlying type, the result is the associated integral value of an enum member.
