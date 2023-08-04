# Introduction to Identity on ASP.NET Core

ASP.NET Core Identity:

- is an API that supports user interface login functionality
- manages users, passwords, profile data, roles , claims, tokens, email confirmation

Identity is typically configured using a SQL Server database to store user names, passwords, and profile data. Alternatively, another persistent store can be used, for example, Azure Table Storage.

## Log in

The Login form is displayed when:

The Log in link is selected.
A user attempts to access a restricted page that they aren't authorized to access or when they haven't been authenticated by the system.
When the form on the Login page is submitted, the OnPostAsync action is called. PasswordSignInAsync is called on the _signInManager object.

## Log out

The Log out link invokes the LogoutModel.OnPost action.

The microsoft articles mentiones the way to use templates to start working on authentication and autharization
