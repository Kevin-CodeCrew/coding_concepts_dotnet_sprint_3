###### Top
###### [Back to Concepts](./README.md)
# Razor Views
Views represent the `V` in `MVC` and are used to present data to the user. They can contain plain HTML, or a combination of HTMl with C#.

## Passing Data to Views
Avoid using `ViewData` and `ViewBag`to pass data to a view whenever possible as they are fragile and do not enforce strong data typing. You have to do extra casting, which makes your code ugly and harder to maintain. 

A better approach is to pass a model (or a view model that references multiple entity models) directly to a view:

```return	View(movie);```

Then in our View, we add a reference to the model type we will be passing in using `@model` and the `@Model` reference in our view to access properties of the model.
```
@model Lecture.Models.WriterModel
<h1>View One</h1>
<table class="table">
    <thead>
        <tr>
        <th scope="col">ID</th>
        <th scope="col">Name</th>
        <th scope="col">Age</th>
        <th scope="col">Is Published</th> 
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scrope="row">@Model.id</th>
            <td>@Model.fName @Model.lName</td>
            <td>@Model.age</td>
            <td>@Model.isPublished</td>
        </tr>   
    </tbody>
</table>
```

## Razor View Syntax
Razor views (files with the `.cshtml` extension) allow us to embed C# code along side our HTML in our views. This adds ooportunities for advanced functionality, including conditionally rendering content using C# patterns we are already familar with.
```
@if (…)	
{
	// C# code	or HTML
}	

@foreach(whatever)
{
	// Output something for each item
}	
```

Render a class (or any attributes) conditionally (here using a ternary  operator as opposed to a standard `if` statement).
```
@{
  string className = Model.Customers.Count > 5 ? “popular” : null;
}

<h2	class=“@className”>whatever content we wish to style</h2>	
```

Razor templates, like plain HTML supports the use of comments and comments are *always* encouraged. However, the syntax differs from that of a standard HTML comment.

Instead of this `<!-- This view is used to render this sort of data for the user -->` we use this format for comments inside of a Razor template `@* This view is used to render this sort of data for the user *@`

**QUICK NOTE: Auto-Reload Views**

Did you get tired of stopping and restarting your server every time you make a change? There's a helpful package for you so that when you're only making changes to your view, you don't have to manually stop and restart your server.

To install it right click on the project name and select Manage Nuget Packages. Search for and install
```Microsoft.AspNetCore.MVC.Razor.RuntimeCompilation```

Then go to `Startup.cs` and change this line `services.AddControllersWithViews();` to this

```csharp
services.AddControllersWithViews().AddRazorRuntimeCompilation();
```

And you're good to go. To see changes made in your view, just save your cshtml file are refresh your browser. It'd be nice if we could also automatically refresh when we make changes to our controllers and other components.... but for now this will have to do....


### General Resources 
- [.NET MVC Forms](.)

[Back to Top](#Top)
