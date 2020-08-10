###### Top
###### [Back to Concepts](./README.md)
# Conditionals

If-Else Statement
```c#
int correctNum = 10; // define an integer
// prompt the user to enter a number in the console
Console.Write("Guess a number : "); // using Write instead of WriteLine doesn't start a new line after the output
// save the user input from the console
string userGuess =  Console.ReadLine(); 
// convert the userGuess from a string to an integer in order to compare the values
int userNum;
Int32.TryParse(userGuess, out userNum); //call the TryParse method and pass in the value to convert and a value to return
// compare values
if(userNum == correctNum)
{
    Console.WriteLine("You guessed the correct number!"); // if values are equal 
} 
else 
{
    Console.WriteLine($"You did NOT guess the correct number.\nThe correct number is {correctNum}"); // if values are not equal
}
```
SwitchCase
```c#
Console.WriteLine("Who is the greatest instructor of all time?"); // prompt the user to enter an instructor name
string userInput = Console.ReadLine(); // save user input from the console
// switch case comparing the value of the user input
switch(userInput)
{
    case "Autumn":
    Console.WriteLine("You entered a pretty good instructor, but not the greatest of all time"); // if the user inputs "Autumn"
    break;
    case "Kenn":
    Console.WriteLine("This instructor has moved on to Greener Mountains ;) "); // if the user inputs "Kenn"
    break;
    case "Kevin":
    Console.WriteLine("YEP! You got it ninja"); // if the user inputs "Kevin"
    break;
    default:
    Console.WriteLine("This isn't even an instructor!"); // if the user does not input one of the options above
    break;
}
```

### General Resources 
- [Conditionals - If Else](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/if-else)

[Back to Top](#Top)