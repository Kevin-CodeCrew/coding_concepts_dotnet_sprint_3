###### Top
###### [Back to Concepts](./README.md)
# Conditionals
An if statement identifies which statement to run based on the value of a Boolean expression. In an if-else statement, if condition evaluates to true, the then-statement runs. If condition is false, the else-statement runs. Because condition can’t be simultaneously true and false, the then-statement and the else-statement of an if-else statement can never both run. After the then-statement or the else-statement runs, control is transferred to the next statement after the if statement. In an if statement that doesn’t include an else statement, if condition is true, the then-statement runs. If condition is false, control is transferred to the next statement after the if statement.

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
`switch` is a selection statement that chooses a single switch section to execute from a list of candidates based on a pattern match with the match expression. The switch statement is often used as an alternative to an if-else construct if a single expression is tested against three or more conditions. The match expression provides the value to match against the patterns in case labels.
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
- [Switchcase](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/switch)

[Back to Top](#Top)
