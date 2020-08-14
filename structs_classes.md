###### Top
###### [Back to Concepts](./README.md)
# Structs and Classes

### Define a Class
```c#
/// <summary>class <c>PetClass</c>
/// Class with properties Name, Age, Type, and Trained(bool)
/// </summary>
class PetClass  
{
    // define properties of the class (specifying the type)
    // more often than not these values will be protected or private to limit access/visibility
    public string name;
    public int age;
    public PetType type; // enum
    public bool trained;
    // define a constructor - a class constructor is names the same as the class and does not have a return type
    public PetClass(string name, int age, PetType type, bool trained)
    {
        // set the values of the object properties to the constructor parameters
        this.name = name;
        this.age = age;
        this.type = type;
        this.trained = trained
    }
    // you can also define methods in a class, like a method to output the properties of a class instance to the console
}
```
### Create an Instance of a Class
```c#
PetClass pet1 = new PetClass("Dakota", 10, PetType.dog, false); // create a new instance of the class

// Access each property of the new pet object using dot notation
Console.WriteLine($"Congrats on your new {pet1.Type}! {pet1.Name} is {pet1.Age} years old. It is {pet1.Trained} that they are trained.");
```
### Define Properties of an Instance of a Class
```c#
// define the properties of a pet object using dot notation
pet1.Name = "Dakota";
pet1.Age = 9;
pet1.Type = PetType.dog;  
pet1.Trained = true;
```
### Access Properties of an Instance of a Class
```c#
// Access each property of the new pet object using dot notation
Console.WriteLine($"Congrats on your new {pet1.Type}! {pet1.Name} is {pet1.Age} years old. It is {pet1.Trained} that they are trained.");
```

### General Resources 
- [Classes and Structs Overview](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/)
- [Properties](https://codeasy.net/lesson/properties)

[Back to Top](#Top)
