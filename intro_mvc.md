###### Top
###### [Back to Concepts](./README.md)

# Intoduction to ASP.NET MVC

## What is MVC?

What is the MVC pattern?
The Model-View-Controller (MVC) architectural pattern separates an application into three main groups of components: Models, Views, and Controllers. This pattern helps to achieve separation of concerns. Using this pattern, user requests are routed to a Controller which is responsible for working with the Model to perform user actions and/or retrieve results of queries. The Controller chooses the View to display to the user, and provides it with any Model data it requires.

The following diagram shows the three main components and which ones reference the others:

![MVC Components](./mvc.png)

## Model Responsibilities
The *Model* in an MVC application represents the state of the application and any business logic or operations that should be performed by it. Business logic should be encapsulated in the model, along with any implementation logic for persisting the state of the application. Strongly-typed views typically use ViewModel types designed to contain the data to display on that view. The controller creates and populates these ViewModel instances from the model.

## View Responsibilities
*Views* are responsible for presenting content through the user interface. They use the Razor view engine to embed .NET code in HTML markup. There should be minimal logic within views, and any logic in them should relate to presenting content. If you find the need to perform a great deal of logic in view files in order to display data from a complex model, consider using a View Component, ViewModel, or view template to simplify the view.

## Controller Responsibilities
*Controllers* are the components that handle user interaction, work with the model, and ultimately select a view to render. In an MVC application, the view only displays information; the controller handles and responds to user input and interaction. In the MVC pattern, the controller is the initial entry point, and is responsible for selecting which model types to work with and which view to render (hence its name - it controls how the app responds to a given request).

## What is ASP.NET Core MVC
The ASP.NET Core MVC framework is a lightweight, open source, highly testable presentation framework optimized for use with ASP.NET Core.

ASP.NET Core MVC provides a patterns-based way to build dynamic websites that enables a clean separation of concerns. It gives you full control over markup, supports TDD-friendly development and uses the latest web standards.

## Creating a Barebones MVC Starter Application
Depending on the IDE you are using, you may have multiple menu options for generating a new MVC application. Here we will stick to using the Command Line Interface (CLI) which can be used with any environment.

`dotnet new mvc`

Will create a barebones .NET MVC web application. Other variations include:
* .NET MVC with .NET authentication using sqlite:
`dotnet new mvc -o YourProjectDirectory -au Individual`

* .NET MVC with .NET authentication using local SQL Server:
`dotnet new mvc -o YourProjectDirectory -au Individual -uld`

* .NET Razor application with .NET authentication using local SQL Server:
`dotnet new webapp -o YourProjectDirectory -au Individual -uld`


### General Resources 
- [ASP.NET MVC Pattern](https://dotnet.microsoft.com/apps/aspnet/mvc)
- [MVC Pattern Detailed Image](./MVC.png)

[Back to Top](#Top)
