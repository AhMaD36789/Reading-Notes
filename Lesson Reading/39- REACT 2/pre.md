# Conditional Rendering

In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state of your application. This is known as conditional rendering. It works the same way conditions work in JavaScript.

## Lists & Keys

When you want to render a list of items in React, you can use an array’s .map() method. Keys are a special string attribute you need to include when creating lists of elements in React. They help React identify which items have changed, are added, or are removed.

## Forms

In HTML, form elements such as < input>, < textarea>, and < select> typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with setState().

## Lifting State

Sharing state is accomplished by moving it up to the closest common ancestor of the components that need it. This is called “lifting state up”. So instead of trying to sync the state between different components, you should rely on the top-down data flow.

## Composition vs Inheritance

React has a powerful composition model, and it’s recommended to use composition instead of inheritance to reuse code between components. In React, you can use props to pass components and functions as children or other props to a component.

## Thinking in React

Thinking in React involves thinking about your app’s components, their hierarchies, and states. It involves breaking down your application into a component hierarchy and building static versions of your app that renders your data model.
