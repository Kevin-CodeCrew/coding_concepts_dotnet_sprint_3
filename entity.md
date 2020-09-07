###### Top
###### [Back to Concepts](./README.md)
# Entity Framework
In this course we have handled persisted data in the context of data access in a .NET MCV application against an SQLite database using Entity Framework. Entity Framework (EF) Core can serve as an object-relational mapper (O/RM), enabling .NET developers to work with a database using .NET objects, and eliminating the need for most of the data-access code they usually need to write.With EF Core, data access is performed using a model. A model is made up of entity classes and a context object that represents a session with the database, allowing you to query and save data. You can use EF Migrations to create a database from your model, and then evolve it as your model changes over time. Instances of your entity classes are retrieved from the database using Language Integrated Query (LINQ).

## Steps to Utilize EF Core
There is some set up required to get an MVC application ready to persist data. Most importantly creating the models and context for that database. The steps to go from a standard MVC application to an application with an SQLite database are listed below. 

- add the required Entity Framework packages to your MVC application by running the commands below in the terminal
```
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.Sqlite
```
- create any models to be represented in database sets in your database context
     - it's important that each property uses the short hand `{get;set;}` and that each model has an integer property `id` or a specified `key` property 
- create a database context 
	- this class extends the base class DbContext imported from `Microsoft.EntityFrameworkCore`
	- this class constructor extends the base constructor passing `options` define as type `DbContextOptions<DBContextClassName>`
	- this class has public database set properties `DbSet<ModelToReference>`
- update the `appsettings.json` file to include `ConnectionStrings` property
```
{
	...

  "ConnectionStrings" : {
    "DefaultDbConnection" : "DataSource=databaseFileName.db"
  }
}
```
- update the `Startup.cs` file to include reference to created database context and connection string in the `ConfigurationServices` method
```c#
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllersWithViews();
    // add db context
    services.AddDbContext<DBContextClassName>(options => options.UseSqlite(Configuration.GetConnectionString("DefaultDbConnection")));
}
```
- add migrations for initial creation by running the command below in the terminal
```
dotnet ef migrations add uniqueMigrationMessage
```
- apply migrations by running the command below in the terminal
```
dotnet ef database update
```
- open the SQLite explorer from the command pallet and select the data source file specific in the app setting file to view created database
- create a reference to the database in any controller needing access to this reference by defining a private readonly property `_context` and set the value of this property in the controller class constructor 
### Model Annotations
Take advantage of the Data Annotation Model Binder to perform validation within an ASP.NET MVC application. The advantage of using the Data Annotation validators is that they enable you to perform validation simply by adding one or more attributes – such as the Required or StringLength attribute – to a class property. To use data annotations import `System.ComponentModel.DataAnnotations;`
```c#
using System;
using System.ComponentModel.DataAnnotations;
// example database model
namespace Practice.Models
{
    public class DatabaseModel
    {
        [Key] // signifies primary key
        public int id{get;set;}
        [Required] // an instance of this model cannot be created without a value for this property
        [StringLength(1000, MinimumLength = 50)] // the value of this property must be between 50 and 1000 characters
        public string itemName{get;set;}
        [Range(0,1000)]  // an instance of this model cannot be created without a value for this property
        public string itemNumber{get;set;} // the value of this property must between 1 and 1000
    }
}
```
### Model Binding

In the following example, only the specified properties of the Instructor model are bound when the OnPost method is called:
```c#
[HttpPost]
public IActionResult OnPost([Bind("LastName,FirstMidName,HireDate")] Instructor instructor)
```
### Model State Error Output
```c#
// method to capture model state validation errors
public static List<string> GetErrorListFromModelState(ModelStateDictionary modelState)
{
    IEnumerable<string> query = from state in modelState.Values
		from error in state.Errors
		select error.ErrorMessage;

    List<string> errorList = query.ToList();
    return errorList;
}
```
### General Resources 
- [Tutorial Console App](https://docs.microsoft.com/en-us/ef/core/get-started/?tabs=netcore-cli)
- [Overview](https://docs.microsoft.com/en-us/ef/core/)
- [Model Binding](https://docs.microsoft.com/en-us/ef/core/)

[Back to Top](#Top)
