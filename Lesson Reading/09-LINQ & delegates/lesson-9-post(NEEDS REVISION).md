# DELEGATES

Delegates are used to pass methods as arguments to other methods. Event handlers are nothing more than methods that are invoked through delegates

## LAMPDA

A lambda expression in C# is an anonymous function that can contain either an expression or a bunch of statements. The operator used to implement a lambda expression is =>. The lambda expression consists of two parts: the left side specifies the input parameters (if any), while the right side is the expression or statement block

(int x, int y) => { return x + y; }

You can use lambda expressions in any code that requires instances of delegate types or expression trees

## LINQ EXTENTION METHODS

LINQ extension methods are methods that add query functionality to the existing System.Collections.IEnumerable and System.Collections.Generic.IEnumerable< T> types

To use the standard query operators, you need to bring them into scope with a using System.Linq directive. Then, any type that implements IEnumerable< T> appears to have instance methods such as GroupBy, OrderBy, Average, and so on

The expression in parentheses is a lambda expression. Many standard query operators take lambda expressions as parameters

## LINQ QUERY OPERATOR

LINQ query operators are methods that form the LINQ pattern. They provide query capabilities including filtering, projection, aggregation, sorting, and more
