###### Top
###### [Back to Concepts](./README.md)
# Authentication and Authorization (ASP.Net Identity Framework)
So far in this course we have developed lists to display data and forms for users to enter data and submit it. These items were unprotected meaning any user with the correct URL for the endpoint/action could access them without requiring a login. This isn't practical or safe in real-world web applications so here we will discuss how we can use ASP.Net Identity framework to secure web applications.

### ASP.Net Identity
- Token based
- Password Hash
- Supports 2 factor authentication (e.g. where a login required *and* the user must also submitted a randomly generated code sent to their email or mobile device)

## Authentication vs. Authorization
Many developers often confuse these two terms, but they do indeed mean very different things.
- Authentication - Is the means by which we confirm the User is who they say, usually by requiring them to login
- Authorization - Determines what an authenticated User *can do* once they are in the system

### Role-based or Policy-based authorization 
- Role-based authorization is a declarative way to restrict access to resources. You can specify the roles that the current user must be a member of to access a specified resource.
- Policy-based authorization involves defining multiple criteria. Essentially, a policy consists of one or more requirements and is usually registered at application startup in the ConfigureServices() method of the Startup.cs file. To apply the policies in your controllers or action methods, you can take advantage of the `AuthorizeAttribute` attribute or the `AuthorizeFilter` filter.

## Starting an MVC application with ASP.Net Identity support
Best to add when MVC application created using *Identity Scaffolding*.
```
	dotnet new mvc -o authintroApp *--auth individual*
```

- Note the additions made to .csproj to support authentication
- Review the tables in Sqlite


### Adding Security Checks

Some code changes are required to support role-based authentication/authorization. Update code added when MVC application generated with basic authentication/authorization in `startup.cs` to require authentication.

```
services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
.AddRoles<IdentityRole>()
.AddEntityFrameworkStores<ApplicationDbContext>();
```

Add this additional code within same method:
```
services.AddMvc(obj =>
{
	var policy = new AuthorizationPolicyBuilder()
		.RequireAuthenticatedUser()
		.Build();
});
```
### Using annotation for authentication requirements in controller
```
using Microsoft.AspNetCore.Authorization;
```
Entire controller (at the top)
```[Authorize]```
Specific Methods
```
[Authorize]
[HttpGet]
public IActionResult AddMemberForm()
{
	return View();
}
```
Specific Controllers/Methods by user role
```[Authorize(Roles=”admin”)]```


### General Resources 


[Back to Top](#Top)
