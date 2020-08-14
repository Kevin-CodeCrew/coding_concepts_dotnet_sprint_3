###### Top
###### [Back to Concepts](./README.md)
# Arrays and Lists
Arrays and lists are similar is structure in that both are a strongly typed collection of items with a zero based index. Arrays cannot be altered or extended after creation. Lists are able to be altered and extended and built in methods such as Add, Remove, and Sort make these alteration much simpler.

Defining an Array of Strings and and Array of Integers
```c#
int[] intArray = new int[]{1,3,5,7,9}; // define an array of integers
string[] strArray = new string[]{"Autumn", "Erin", "Kevin", "Meka"}; // define an array of strings
```
Array Properties - Accessing Elements and Length
```c#
// Access elements of an array by index position and return length of array using Length method
Console.WriteLine($"The second element in the intArray is {intArray[1]} and the array is {intArray.Length} elements long");
Console.WriteLine($"The second element in the strArray is {strArray[1]} and the array is {strArray.Length} elements long");
```
Defining a List of Integers - Using `Add()`

Add - Adds an object to the end of the List<T>.
```c#
List<int> intList = new List<int>(); // declare a list of integers
// add integers to the list
intList.Add(8);
intList.Add(6);
intList.Add(2);
intList.Add(4);
```
Defining a List of Strings - Using `Add()`

Add - Adds an object to the end of the List<T>.
```c#
List<string> strList = new List<string>(); // declare a list of strings
// add strings to the array
strList.Add("Damien");
strList.Add("JP");
strList.Add("Jeffery");
```
Defining a List of Strings 

A list of strings can be populated when declared using the {} shorthand
```C#
List<string> strList = new List<string>(){"Damien", "JP", "Jeffery"};
```
List Properties - Accessing Elements and Length
```c#
// Access elements of a list by index position and return length of array using Count method
Console.WriteLine($"The second element in the intList is {intList[1]} and the array is {intList.Count} elements long");
Console.WriteLine($"The second element in the strList is {strList[1]} and the array is {strList.Count} elements long");
```
List Methods - `Sort()` and `Remove()`

Sort - Sorts the elements or a portion of the elements in the List<T> using either the specified or default IComparer<T> implementation or a provided Comparison<T> delegate to compare list elements.

Remove - Removes the first occurrence of a specific object from the List<T>.

IndexOf - Finds the 0 based index of the  first occurrence of a specific object from the List, retruns -1 if no object is found

Contains - Returns a value indicating whether a specified object occurs within the List
```c#
// List Sort method
intList.Sort();

// List Remove method
strList.Remove("Damien");

// List IndexOf method
strList.IndexOf("Jeffery")

// List Contains method
strList.Contains("JP")
```
### General Resources 
- [Collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)
- [Arrays](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/)

[Back to Top](#Top)
