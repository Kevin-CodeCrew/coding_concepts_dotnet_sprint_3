###### Top
###### [Back to Concepts](./README.md)

# ASP.NET Web API Controllers/Routing

## What is a Controller?

ASP.NET MVC applications use several conventions to help you quickly write an API controller to handle web requests foro the resources you expose from your database. Let's look at an example.

In your browser code, whether you built a React, Angular, Vue, or other JavaScript based application, you often make XHRs to get data from other locations on the Web. Since you are going to be building this "other location" now, your JavaScript application could make a request to your API.

Assume your API is listening to requests on port 5000 of your machine. It exposes kitchen appliances as a resources (e.g. toaster, coffee maker, microwave, etc.) you could interact with aa language like JavaScript by coding something similar to the following.

### JavaScript Request

This code requests the `/appliance` resource from your API.

```js
fetch("http://localhost:5000/appliances")
  .then(res => res.json())
  .then(appliances => {
    appliances.forEach(appliance => {
      document.querySelector(".applianceList").innerHTML += `<p>${
        appliance.name
      }</p>`;
    });
  });
```

### C# Controller Method

This code handles `GET` requests for the `/appliances` request. It established a connection to the database, performs a SQL query to get all appliances and stores the results in an `appliances` variable, and then generates a response using the `Ok(appliances)` method.

ASP.NET will automatically convert the `IEnumerable` into JSON format so that the JavaScript code (see above) that made the request can parse it as JSON.

```cs
[Route("api/[controller]")]
[ApiController]
public class AppliancesController : ControllerBase
{
    [HttpGet]
    public async Task<IActionResult> Get()
    {
        using (SqlConnection conn = Connection)
        {
            conn.Open();
            using (SqlCommand cmd = conn.CreateCommand())
            {
                cmd.CommandText = $"SELECT Id, Manufacturer, Model FROM Appliance";
                SqlDataReader reader = cmd.ExecuteReader();

                List<Appliance> appliances = new List<Appliance>();

                while (reader.Read())
                {
                    Appliance appliance = new appliance
                    {
                        Id = reader.GetInt32(reader.GetOrdinal("Id")),
                        Manufacturer = reader.GetString(reader.GetOrdinal("Manufacturer")),
                        Model = reader.GetString(reader.GetOrdinal("Model"))
                    };
                    appliances.Add(appliance)
                }
                reader.Close();

                /*
                    The Ok() method is an abstraction that constructs
                    a new HTTP response with a 200 status code, and converts
                    your IEnumerable into a JSON string to be sent back to
                    the requessting client application.
                */
                return Ok(appliances);
            }
        }
    }
}
```
## Query String and Route Parameters

You can send data to the server in your request in three main ways.

1. In the body of the request.
1. As a route parameter.
1. As a query string parameter.

## Request Body

You learned how to do this in JavaScript using `fetch`. Here's a JavaScript request to your `cohorts` resource in your API.

```js
fetch("http://localhost:5000/cohorts", {
    "method": "POST",
    "headers": {
        "Content-Type": "application/json"
    },
    "body": JSON.stringify({
        "name": "Day 26"
    })
})
.then(res => res.json())
.then(console.table)
```

You can view the body request by looking in your Network tab of Chrome Developer Tools, clicking on the request, and scrolling to the bottom.

![a sample fetch request and showing the request payload](./dev_console_network_tab.gif)

## Route Parameters

A route parameter is part of the route itself. For example, if you want to get a single student, you would GET the following URL.

```sh
http://localhost:5000/students/1
```

The `1` at the end of the URL is a route parameter.

This kind of parameter is handled in a controller method by specifying the `[FromRoute]` attribute in the argument list. The following method will create a variable `id` and store the value of `1` in it.

```cs
public async Task<IActionResult> Get([FromRoute]int id)
```

## Query String Parameters

Anything after the route and preceded by a question mark is a query string parameter.

```sh
http://localhost:5000/students?cohort=13
```

The `cohort` in the URL above is a query string parameter. It's value is `13`. You can provide as many query string parameters as you want.

```sh
http://localhost:5000/students?cohort=13&orderBy=lastname&limit=5
```

To get the value of each of those query string parameters, you specify each in the argument list. Any arguments with no attribute in front of them will instruct ASP.NET to look in the query string parameters for the values.

> **Note:** The variable names you define in the argument list must match the name in the URL. If you changed `string orderBy` to `string orderColumn`, then it would not capture `lastname` from the URL above.

```cs
public async Task<IActionResult> Get(int? cohort, string orderBy, int limit)
```

You can read the [Handle requests with controllers in ASP.NET Core MVC](https://docs.microsoft.com/en-us/aspnet/core/mvc/controllers/actions?view=aspnetcore-2.1) article to learn more about using controllers.

### General Resources 
- [ASP.NET MVC Pattern](https://dotnet.microsoft.com/apps/aspnet/mvc)
- [ASP.NET MVC Routing Overview](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions-1/controllers-and-routing/asp-net-mvc-routing-overview-cs)

[Back to Top](#Top)
