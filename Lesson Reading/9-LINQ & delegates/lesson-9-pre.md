# Language Integrated Query (LINQ)

(LINQ) is the name for a set of technologies based on the integration of query capabilities directly into the C# language.

queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.

The LINQ family of technologies provides a consistent query experience for objects (LINQ to Objects), relational databases (LINQ to SQL), and XML (LINQ to XML).

the most visible "language-integrated" part of LINQ is the query expression. Query expressions are written in a declarative query syntax. By using query syntax, you can perform filtering, ordering, and grouping operations on data sources with a minimum of code

You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports IEnumerable or the generic IEnumerable< T> interface.

## Query expression overview

- Query expressions can be used to query and to transform data from any LINQ-enabled data source.
- Query expressions are easy to grasp because they use many familiar C# language constructs.
The variables in a query expression are all strongly typed, although in many cases you do not have to provide the type explicitly because the compiler can infer it.
- A query is not executed until you iterate over the query variable
- At compile time, query expressions are converted to Standard Query Operator method calls according to the rules set forth in the C# specification. Any query that can be expressed by using query syntax can also be expressed by using method syntax.
- As a rule when you write LINQ queries, we recommend that you use query syntax whenever possible and method syntax whenever necessary. Query expressions are often more readable than equivalent expressions written in method syntax.
- Some query operations, such as Count or Max, have no equivalent query expression clause and must therefore be expressed as a method call. Method syntax can be combined with query syntax in various ways.
- Query expressions can be compiled to expression trees or to delegates, depending on the type that the query is applied to. IEnumerable< T> queries are compiled to delegates. IQueryable and IQueryable< T> queries are compiled to expression trees.

## Three Parts of a Query Operation

1. Obtain the data source.

1. Create the query.

1. Execute the query.

### the data source

A query is executed in a foreach statement, and foreach requires IEnumerable or IEnumerable< T>. Types that support IEnumerable< T> or a derived interface such as the generic IQueryable< T> are called queryable types.

### the query

The query specifies what information to retrieve from the data source or sources. Optionally, a query also specifies how that information should be sorted, grouped, and shaped before it is returned. A query is stored in a query variable and initialized with a query expression.

The query expression contains three clauses: from, where and select. (If you are familiar with SQL, you will have noticed that the ordering of the clauses is reversed from the order in SQL.) The from clause specifies the data source, the where clause applies the filter, and the select clause specifies the type of the returned elements.

### query execution

#### Deferred Execution

the query variable itself only stores the query commands. The actual execution of the query is deferred until you iterate over the query variable in a foreach statement. This concept is referred to as deferred execution

The foreach statement is also where the query results are retrieved.

Because the query variable itself never holds the query results, you can execute it as often as you like.

#### Forcing Immediate Execution

Queries that perform aggregation functions over a range of source elements must first iterate over those elements. Examples of such queries are Count, Max, Average, and First. These execute without an explicit foreach statement because the query itself must use foreach in order to return a result. Note also that these types of queries return a single value, not an IEnumerable collection.

## Basic LINQ Query Operations

### Obtaining a Data Source

In a LINQ query, the first step is to specify the data source. In C# as in most programming languages a variable must be declared before it can be used. In a LINQ query, the from clause comes first in order to introduce the data source

### filtering

Probably the most common query operation is to apply a filter in the form of a Boolean expression. The filter causes the query to return only those elements for which the expression is true. The result is produced by using the where clause. The filter in effect specifies which elements to exclude from the source sequence.

### ordering

Often it is convenient to sort the returned data. The orderby clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.

### grouping

The group clause enables you to group your results based on a key that you specify.

When you end a query with a group clause, your results take the form of a list of lists. Each element in the list is an object that has a Key member and a list of elements that are grouped under that key. When you iterate over a query that produces a sequence of groups, you must use a nested foreach loop. The outer loop iterates over each group, and the inner loop iterates over each group's members.

If you must refer to the results of a group operation, you can use the into keyword to create an identifier that can be queried further.

### Joining

Join operations create associations between sequences that are not explicitly modeled in the data sources

In LINQ, you do not have to use join as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.

### Selecting (Projections)

The select clause produces the results of the query and specifies the "shape" or type of each returned element.

For example, you can specify whether your results will consist of complete Customer objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.

When the select clause produces something other than a copy of the source element, the operation is called a projection. The use of projections to transform data is a powerful capability of LINQ query expressions.

### To introduce an identifier by using let

You can use the let keyword to introduce an identifier for any expression result in the query expression. This identifier can be a convenience or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.

### To use method syntax in a query expression

some query operations can only be expressed by using method syntax.
The following code calculates the total score for each Student in the source sequence, and then calls the Average() method on the results of that query to calculate the average score of the class.

    var studentQuery6 =
    from student in students
    let totalScore = student.Scores[0] + student.Scores[1] +
        student.Scores[2] + student.Scores[3]
    select totalScore;

    double averageScore = studentQuery6.Average();
    Console.WriteLine("Class average score = {0}", averageScore);

    // Output:
    // Class average score = 334.166666666667