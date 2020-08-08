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
public string Name;
public int Age;
public PetType Type;
public bool Trained;

}
```
### Create an Instance of a Class
```c#
PetClass pet1 = new PetClass(); // create a new instance of the class
// define the properties of the new pet object
pet1.Name = "Dakota";
pet1.Age = 9;
pet1.Type = PetType.Dog;  // enumerated type define outside of the class
pet1.Trained = true;
// Access each property of the new pet object using dot notation
Console.WriteLine($"Congrats on your new {pet1.Type}! {pet1.Name} is {pet1.Age} years old. It is {pet1.Trained} that they are trained.");
```
### Define Properties of an Instance of a Class
```c#
// define the properties of the new pet object
pet1.Name = "Dakota";
pet1.Age = 9;
pet1.Type = "dog";  
pet1.Trained = true;
```
### Access Properties of an Instance of a Class
```c#
// Access each property of the new pet object using dot notation
Console.WriteLine($"Congrats on your new {pet1.Type}! {pet1.Name} is {pet1.Age} years old. It is {pet1.Trained} that they are trained.");
```

### General Resources 
- [Classes and Structs Overview](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/)

[Back to Top](#Top)
