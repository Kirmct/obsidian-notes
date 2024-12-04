# Compilation
Its a process of transforming the source code, in our case, a \*.cs file into a format that the computer can work with

# DLL→ Dynamic Link Library
Our code compiled in a format that the computer understands
The excecutable file uses the .dll, if we remove the .dll the project dont run
Every code we compile to a .ddl file
![[Pasted image 20240812152759.png]]
# Variables
We can see variables as an box to store values
Has to have a name
In C# variables cant change their type in a natural way
The name has to be unique in the scope that the variable is inside
Inicialization is when we assign a initial value for the variable
## Naming variables & Introduction to Clean Code
We can name them whatever we want
Dont name with reserved words in c#, but if we have and want to, we need to use an at (@)

```C#
string @class = "teste"
```
- C# keyword cant be used as variable names
- The first character cant be a digit
- C# is case sensitive
- PascalCase
### Tips
- Avoid abbreviations → birthday is better than bd
- Be precise → firstName, lastName are better than name1, name2
- Take your time
- You can always rename a variable to something better

# Operators
## Arithmetic
+ - * / %
## Boolean
We have a kind of variable that check if a condition is true or false, in a database can ben assigned as a bit;
```C#
int number = 10; bool isHigherOrEqualTo5 = number >= 5;
```
### AND and OR logical
We have two kind of operatos, one of then checks if all setence is true or false, and the other check if any condition match
```C#
int number = 10; bool isHigherTo5AndIsEvenOrHigherThan50 = number > 50 || (number > 5 && number % 2 != 0) ; //pay attention that we put the litghweitgh condition first //its a good choice cause if the first match the condition the other part will not be processe //with it the code is more optimized
```
### IF and ELSE
Those are conditionals statement, to build a scope of code
They combine if logical operators to verfiy if something have to happen

```C#
if(true) 
{
	//code here 
}else 
{ 
	//code here 
}
```
## += , ++, --, etc
```C#
//we need to initialize the variable, if not a error can be throw
var number = 10;
number++; //11
number+= 2; //13
number--; //12
number-= 2; //10
//etc
```
# The scope of local variable
Defines a part of our programn where some particular variables is accessible
# Methods
Methods are scopes of code that can return something or nothing
## Void methods
Are methods without return
## Non void methods
Are methods that return something, can be a int, bool, a class, etc
All paths in a non void method must return a value
# Statically and Dynamically Types
C# is a statically typed language
They cant change by herself a variable type
## Parsing 
Parsing is a way to change a value to another
### String to int example
we can change a string for a int type using parsing
```C#
string valor = "123"; int convertedValor = int.Parse(valor);
```
## TryParse
This method uses the out keyword

Return a bool if is possible to parse, but also return a value if is possible

To understand better, we need to know about [Exceptions and Erros], gonna see ahead
```C#
var input - Console.ReadLine();
bool isParsingSuccess = int.TryParse(
	input, out int number); //declaring the possible return here
if(isParsingSuccess)
	Console.WriteLine("Success");
else
		Console.WriteLine("Not success");
```
# Exceptions and Errors
Exceptions are the representation of runtime errors
We have to previne this exceptions
If any of then happen, the application will broke
## Runtime Errors
Happen when the application is runing
## Compilation Errors
Happen during the compilation
# Switch statement
```C#
switch (dayNumber) 
{ 
	case 1: 
	case 2: 
	case 3: 
	case 4: 
	case 5: 
		return "Working day"; 
	case 6: 
	case 7: 
		return "Weekend"; 
	default: return "Invalid day number"; 
	}
```

```C#
switch (userChoice.ToUpper()) //variable that will be used
{
    case "s"://we can use this double case with the same result
    case "S":
        PrintSelectedOption("S");
        break;
    case "E":
        PrintSelectedOption("E");
        break;
    case "R":
        PrintSelectedOption("R");
        break;
    case "A":
        PrintSelectedOption("A");
        break;
    default: //default methos is return if any setence before are abble
        PrintSelectedOption("Invalid");
        break;
}
```

# Loops
Repeat a code block
Execute code multiple times
## While
Executed as a conditions is invalid
```C#
var number = 0;

while(number < 10)
{
    number++;
    Console.WriteLine("Number is: " + number);
}
```
## do while
Similar to while loop, but in do while loop the condition is checked after the start of the loop
So at least once time the code block will run
```C#
var number = 0;

do
{
    Console.WriteLine("Number is: " + number);
    number++;
}
while(number < 10)

```

## For
Execute some code give a number of times
```C#
for(int i = 0; i < 5; ++i)//initialization, conditon, iterator
{
	//code here
}
```
Be carefull if the condition can be finish, if not the code will break with a time exception or memorie exception
## Break
Stop the loop and go out
```C#
for(int i = 0; i < 5; ++i)//initialization, conditon, iterator
{
	//code here
	if(i == 3)
		break;
}
```

## Continue
```C#
for(int i = 0; i < 5; ++i)//initialization, conditon, iterator
{
	//code here
	if(i % 3 == 0)
		continue;
}
```
## Foreach
Simply iterates a collection, used when we dont need the index
We can see mor about collections on [Lists] topic ahead
```C#
foreach(var word in words)
{
	Console.WriteLine(word);
}
```
# Arrays
Most basic collaction type in C#
Like a collection of boxes that have something inside
Once created array cant change the size
Index collections starts with zero 0
```C#
int[] numbers = new int[] {2, 3, 4, 5, 6};
int n = number[^2]; //will take the last position minus 2
Console.WWriteLine(n);
```
## Multidimensional arrays
Arrays can have two, three dimensional arrays etc
```C#
char[,] letters = new char[2,3];
letter[0,0] = 'a';

var letters2 = new char[,]
{
	{'a', 'b'}, //row
	{'c', 'd'}
}

for(int i = 0; i < letters.GetLength(0); i++) //.GetLength(0) -> get the row length
{
	for(int j = 0; i < letters..GetLength(1); i++)
	{
		Console.Writeline(letters2[i,j]);
	}
}
```
# Lists
Used when a collection has to be dynamic
The size is not fixed, we can add or remove elements
```C#
List<string> words = new List<string>(); //list type
Console.WriteLine(words.Count); //the size of the list, similar to Length in arrays
words.add("word"); //adding an element
words.remove("word");//if we pass a element that doesnot exist nothin happen

//we can access a item using him index
words[0] = "xpto"; //if we try to get a element out of list size we get an error
words.RemoveAt(4); //error if doesnt exist this index
//adding range
var newWords = new List<string>{"asd","asdad"}
words.AddRange(newWords);

words.IndexOf("word"); //return the index, if doesnt exists return -1
words.Contains("five"); //return a bool
words.Clear(); // remove all elements
```
# out Keyword
Sometimes we need to return two results from a method instead of one

Generally, it is not a good practice for a method to do two things

When we pass a simple variable as param to a function, we are passing a copy, not a reference, so if we change the value inside the function the original value still the same

If we use the out keyword we pass the variable reference, not the copy, so we change the original value

```C#
//Example of the necessity to return two result
//in a array we want to return only positives numbers
//and how many not positive numbers are too
var numbers = new int[]{ 1, 2, 3, -1, -2};

var nonPositiveCount;//we dont need to declare here, can be declared in the params

var onlyPositive = GetPositives(numbers, out nonPositiveCount);//look here

List<int> GetPositives(
	int[] numbers, 
	out int countOfNonPositive)//look here
{
	countOfNonPositive = 0; //we need to give a value
	var result = new List<int>();
	foreach(var number in numbers)
	{
		if(number > 0)
			result.Add(number);
		else
			countOfNonPositive++;
	}
	return result;
}
```
# IEnumerable<T>
An interface generic that allow only methods that cannot change the state of the list