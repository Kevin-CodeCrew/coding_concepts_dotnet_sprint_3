###### Top
###### [Back to Concepts](./README.md)
# Variables, Input and Output to the Console

### Output to the console
```C#
Console.Write("Hello World"); // Output to the console
```
### Value Type Variable Declarations : Strings, Integers and Booleans
```C#
string myStr = "C# is the best!"; // string variable declaration
int myNum = 100; // integer variable declaration
bool myBool = true; // boolean variable declaration
```
### Value Type : Enumeration  Types
An enumeration type (or enum type) is a value type defined by a set of named constants of the underlying integral numeric type. To define an enumeration type, use the enum keyword and specify the names of enum members
```C#
enum Priority
{
    high, medium, low
}
// access enum member
taskPriority = Priority.high;
```
### Getting and Saving Input from the Console
```C#
Console.WriteLine("What is your favorite programming language");
string userName = Console.ReadLine(); // Input from the console and
Console.WriteLine(userName);
```
### Casting Variable Types
Console.ReadLine() returns a string but that value can be cast to a integer using the Parse method. 
```C#
Console.WriteLine("Enter a number between 1 and 5");
int userNumber = Int32.Parse(Console.ReadLine());
```
### Using String Templating 
```C#
Console.Write("Enter your name:");
string userName;
userName = Console.ReadLine();
Console.WriteLine($"Hello {userName}"); // String Templating
```
### General Resources 
- [Getting Started with C#](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/)
- [Types and Variables](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/types#simple-types)

[Back to Top](#Top)
