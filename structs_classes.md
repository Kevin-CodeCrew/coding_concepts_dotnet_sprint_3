###### Top
###### [Back to Concepts](./README.md)
# Structs and Classes
A type that is defined as a class is a reference type. At run time, when you declare a variable of a reference type, the variable contains the value null until you explicitly create an instance of the class by using the new operator, or assign it an object of a compatible type that may have been created elsewhere. Classes are declared by using the class keyword followed by a unique identifier. The class keyword is preceded by the access level. Because public is used in this case, anyone can create instances of this class. The name of the class follows the class keyword. The name of the class must be a valid C# identifier name. The remainder of the definition is the class body, where the behavior and data are defined. Fields, properties, methods, and events on a class are collectively referred to as class members. A class defines a type of object, but it is not an object itself. An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.Objects can be created by using the new keyword followed by the name of the class that the object will be based on.
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
### Structs
A structure type (or struct type) is a value type that can encapsulate data and related functionality. You use the struct keyword to define a structure type. Structure types have value semantics. That is, a variable of a structure type contains an instance of the type. By default, variable values are copied on assignment, passing an argument to a method, and returning a method result. In the case of a structure-type variable, an instance of the type is copied. Typically, you use structure types to design small data-centric types that provide little or no behavior.
```c#
struct Example
{
    public string description;
    prublic int duration;
    public bool isComplete;
}
Example myStructExample;
myStructExample.description = "A great description";
myStructExample.duration = 25;
myStructExample.isComplete = true;
Console.WriteLine(myStructExample.description)
// --------------Expected Output--------------
// A great Desccription
```
### Inheretence
Classes fully support inheritance, a fundamental characteristic of object-oriented programming. When you create a class, you can inherit from any other interface or class that is not defined as sealed, and other classes can inherit from your class and override class virtual methods. Inheritance is accomplished by using a derivation, which means a class is declared by using a base class from which it inherits data and behavior. A base class is specified by appending a colon and the name of the base class following the derived class name.

```c#
class AdoptedPet : PetClass  
{
    // define properties of the class (specifying the type)
    // more often than not these values will be protected or private to limit access/visibility
    public string ownerName;
    // define a constructor - a class constructor is names the same as the class and does not have a return type
    public PetClass(string name, int age, PetType type, bool trained, string owerName) : base(name, age, type, bool)
    {
        this.ownerName = ownerName;
    }
}
```
### General Resources 
- [Classes and Structs Overview](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/)
- [Properties](https://codeasy.net/lesson/properties)

[Back to Top](#Top)
