###### Top
###### [Back to Concepts](./README.md)
# Forms
So far in this course we have developed forms for users to enter data and submit it using standard HTML, CSS, and JavaScript. This approach is also supported in .NET MVC. However, as we saw earlier, the use of `Razor` templates (`.cshtml`) adds support for additional development options that greatly enhances our web pages. This includes support for developing and using HTML Forms.

HTML Forms in Razor templates fully supports the `code first` approach where we generate many development artifacts directly from our entity models. For HTML forms, this includes generation of form elements, validation, and data binding.

## Razor Markup

- Action to return a view that creates a form

```csharp
@using(Html.BeginForm(“action”,“controller”))
{                
    <div class=“form­‐group”>
        @Html.LabelFor(m => m.Name)
        @Html.TextBoxFor(m =>  m.Name, new 
            {@class = "form-control"})
    </div>
    <button type=“submit” class=“btn btn­‐primary”>
        Save
    </button>
}   

```

`new {@class =“form-control”)}` let's us add additional HTML attributes.

## Labels

### Overriding Labels 
```csharp
Display(Name = “Date of Birth”);
public DateTime ? Birthdate{get;set;};
```
## CheckBoxes
Checkboxes generally need to be styled a bit differently than what is provided from the basic Bootstrap `form-control` class used with other form inputs. In order to display a checkbox properly, we can use Bootstrap classes specific to checkboxes.
```
    <div class="form-check">
        @Html.CheckBoxFor(auth => auth.isActive, new { @class="form-check-input" })
        @Html.LabelFor(auth => auth.isActive, new { @class="form-check-label" })
    </div>
```

## Dropdown Lists

```
@Html.DropDownListFor(m => m.TypeId, new SelectList(Model.Types,“Id”,“Name”),“”,new {@class = “form‐control”}
```

## Model Binding
By binding a model to the form using `@model` we can then bind each form field directly to our entity model definition. This *code first* approach provides additional capabilities to our forms in terms of 

### Saving Data
You can optionally handle both `create` and edit (`update`) in one action by checking what is passed in.

```csharp
[HttpPost]
public ActionResult Save(Customer customer)
{
	if (customer.Id == 0) // No customer ID passed in
	{
		_context.Customers.Add(customer);
	}
	else
	{
		Customer customerInDb = _context.Customers.Single(c.Id == customer.Id);
		//... update properties
	}
	_context.SaveChanges();
	return RedirectToAction(“Index”, “Customers”);
}
```
## Editing Data
TBD

### Updating Data
TBD 

#### Hidden Fields
Required when updating data in that the User will never enter the `id`. We just use it behind the scenes.

```csharp
@Html.HiddenFor(m => m.Customer.Id)
```

## Form Validation
We can leverage the additional metadata provided by using annotations in our entity models to perform sophisticated validation.



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
- [.NET MVC Razor Forms](https://docs.microsoft.com/en-us/aspnet/core/razor-pages/?view=aspnetcore-3.1&tabs=visual-studio)


[Back to Top](#Top)
