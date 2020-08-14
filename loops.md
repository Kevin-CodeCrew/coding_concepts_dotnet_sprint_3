###### Top
###### [Back to Concepts](./README.md)
# For Loops
```c#
List<string> strList = new List<string>(){"Autumn", "Kevin", "Erin", "Meka"};
for(int i = 0; i < strList.Count; i++)
{
    Console.WriteLine($"Staff Member : {strList[i]}");
}
```
# For Each
```c#
List<string> strList = new List<string>(){"Autumn", "Kevin", "Erin", "Meka"};
strList.ForEach(strItem => Console.WriteLine($"Staff Member : {strItem}"));
```
# While Loops
```c#
Console.WriteLine("Enter a sponsor or enter done : "); // prompt
string newSponsor = Console.ReadLine(); // save input 

while(newSponsor != "done") // while user input is not "done" add to list and prompt
{
    this.sponsors.Add(newSponsor); // add to list
    Console.WriteLine("Enter a sponsor or enter done : "); // prompt
    newSponsor = Console.ReadLine(); // update value
}
```
### General Resources 
- [For Loops](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/for)
- [While Loops](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/while)

[Back to Top](#Top)
