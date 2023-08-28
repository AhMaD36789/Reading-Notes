# MVC Pattern

MVC stands for model-view controller. It is a software design pattern that separates the representation of information from its manipulation, so as to improve mod

1. Model: It is the data structure or object that holds all information about our application and its state.

2. Controller :It acts as a mediator between model and view, it controls how user interacts with the system and also communicates to other

3. View :It is a representation of how things should look, feel ,and act in your program to users.
4. Controller: The controller acts as an interface between model and view.

if empty project is not running=>(
package: ASPNETCore.MVC.Razor.Runtime

in program.CS:

builder.Services.AddControllersWithViews().AddRazorRuntimeCompilation();
)

we learnt also about the basics of making a view
