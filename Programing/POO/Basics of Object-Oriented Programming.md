# Procedural Programming
No separation in levels of abstraction
Code in line, composed of procedures, they are called in order of the program
Its hard to make changes, case we need to do something diferente than usual

# What is OOP
Is like building blocks from wich we can compose very complex applications and the code is east to understand and modify
Focuses on the concept of objects contains data and methods
Represents something, like a Person
![[Pasted image 20240812155844.png]]
We create class to represent objects
Code is modular, makes it easier to maintain, reuse and modify
Code is more flexible
Code is easier to understand
Its easy to control how some methods and data can be accessed, less error-prone
# Abstraction
Means that classes expose only essential data and methods, and hide the underlying details
Ex: drive a car, we only have to know how to drive, not how the car works, the engineer etc
## First Class
```C#
class Rectangle //capitalized
{
	int width; //fild is a variable
	int height; //if we dont initialize, they use the default value
}

var rectangle = new Rectangule(5, 10); //only works if we have a constructor
var rectangle2 = new Rectangle(); //default
```
# Data Hiding
Public filds always can be changed, in any part of code
Private filds only can be changed in constructors or methods, they can pass a verification, only inside the class can be accessed
When we make a member non-public is called data hiding
Make public can be a risk
```C#
class Rectangle 
{
	int width; //default is private
	public int height; //public method can be accessed outside the class
}
```

# Custom Constructor
Conventions tha [Microsoft](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions) recomend us to follow
```C#
class Rectangle 
{
	public int Width; 
	public int Height; 
	
	//constructor
	//same class name, no return type, only used when instancioation
	public Rectangle(int width, int height) 
	{
	//have any bussines logic in the constructor is considered an antipattern
	//the exception for this is validation
		Width = width;
		Height = height;
	}
}

//default constructor doesnt work if we have a constructor in class
//except if we create a default constructor in the class
var rectangle2 = new Rectangle(); 
```
# C# restrictions on code outside classes and Top-Level Statements
Virtually all C# code we write must belong to some class
Top-Level Statements is a approach intruduced on new versions of C#, stills a class behind
# Adding methods to classes
The name of a method should always start with a verb
```C#
public class Rectangle
{
    public int Width;
    public int Height;

    public Rectangle(int width, int height)
    {
        Width = width;
        Height = height;
    }

    public int CalculateArea() //the dafault access modifier is always most restrictive
    {
        return (Width * Height);
    }
}
```
# Encapsulation
Bundling data with methods that operate on this data (in single class)
Data and methods are encapsule together

Data hiding means making members of a class non-public, while encapsulation means bundling data with methods that operate on it in the same class. They work together well but are notthe same.
# Method Overloading
Multiple methods with the same name
They have to be distinguable
```C#
 public class MedicalAppointment
 {
     private string _patientName;
     private DateTime _date;

     public MedicalAppointment(string patientName, DateTime date)
     {
         _patientName = patientName;
         _date = date;
     }

     public void Reschedule(DateTime date) 
     {
         _date = date;
     }

     public void Reschedule(int month, int day)//same name 
     {
         _date = new DateTime(_date.Year, month, day);
     }

     public void Reschedule(int monthsToAdd, int daysToAdd) //mistake
     { 
         _date = new DateTime(
             _date.Year, 
             _date.Month + monthsToAdd, 
             _date.Day + daysToAdd); 
     }
 }
```
# Constructor Overloading
```C#
public class Dog
{
    private string _name;
    private int _age;

    public Dog(): this("Unkown") //call another constructor
    {}

    public Dog(string name)
        => _name = name;

    public Dog(string name, int age)
    {
        _name = name;
        _age = age;
    }
}
```
# “this” keyword (current instance reference)
references the object instance, used when we want to do something inside the class
# Optional parameters
If one optional parameters is provided, all the other ones preceding it must be provided too
We use when we can pass or can not pass a value, optional
```C#
public MedicalAppointment(string patientName, int day = 5)
{
	_patientName = patientName;
	_date = Datetime.Now.AddDays(day);
}

var ap = new MedicalAppointment("Kirmct");
var ap2 = new MedicalAppointment("Kirmct", 7);
```
The dafault value of an optional parameter must be compile-time constant
Optional parameters must appear after all required parameters
Ambiguty, optional parameters methods has no preference, will be used the one without optional parameters
## Validation of constructor parameters
Its a good practice to validade the values on the constructor
# Readonly and const
A readonly field can only be assigned at the declaration or in the constructor, after the object is constructed, it will not be possible to change the value of a readonly field
Immutabilty means tha once the object was created we cant change
Good practice: make fields readonly if possible
We use readonly fields when we want a field never to change after it has been set in the constructor

CONST
Const modifier can be applied to both, variables and fields, and must be assigned at declaration and can never be modified afterward, and must be a compile-time constant

We use cont for things witch a constant value, known at compilation time
# Properties
Getter and Setter methods
Capitalized, more simular to methods than fields, their names should be nouns
```C#
//old way
  public int _wight;
  public int Weight
  {
      get
      {
          return _weight;
      }
      set
      {
          if(value > 0)
	          _weight = value;
      }
  }
```
Are diferents from fields cause we can use diferents access methods
```C#
  public int _wight;
  public int Weight
  {
      get
      {
          return _weight;
      }
      private set
      {
          if(value > 0)
	          _weight = value;
      }
  }
```
Bew Way
```C#
//new way
public int MyProperty { get; private set; }
//this way stills works simular the old, but behind 
//we use the old way if we want more controll about somenthing
```
# Object initializers
We dont need to put all properties when we use object initializers
If the setter are not present or were are private, object initializer will not work
```C#
public class Person
{
    public string Name { get; set; }
    public int YerOfBirth { get; set; }
    
    public Person(string name)
    {
	    Name = name;
    }
}

var person = new Person("kirm")
{
	YerOfBirth = 98;
};
```
Using the method init, we can assigne a value only object creation, after that will work as they dont have setter
```C#
public class Person
{
    public string Name { get; set; }
    public int YerOfBirth { get; init; }}
}

var person = new Person
{
	YerOfBirth = 98;
};
```
# Static methods and class
A mathematic class, only contains methods, no data
Or data can be const
When we dont need to create a instance of a class
Static methods belong to a class as a whole, not a specific instance
Static methods cant use the instance data (value of fields or returned by properties)

A static class cannot be instantiated; it only works as a container for methods
Static classes can only contain static methods

Non-static classes can contain static methods
If a private method doesnt use instance data, make it static
All const fields are impliced statics

```C#
public static class Calculator
{
    const double PI = 3.14;

    public static double Add(double a, double b) => a + b;
    public static double Subtract(double a, double b) => a - b;
    public static double Multiply(double a, double b) => a * b;
}

public class NumberToDayOfWeekTranslator
{
    public static readonly string[] WeekDays = 
        { "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" };

    public static string Translate(int number)
        => number >= 1 && number <= 7 ? WeekDays[number - 1] : "Invalid day of the week";
}
```

# Static fields, properties and constructors
Static and non-static classes can contains static fields and properties
Are used when we need to share some information to all intances of the class
Have static fields and properties can be risk, and must be avoided if possible
```C#
public class Rectangle 
{
    public static int CountOfInstances { get; private set; }
    public static DateTime _firsUsed;

    static Rectangle() //happen on the first instance of the containing class is created
    {
        _firsUsed = DateTime.Now;
    }

    public Rectangle(int width, int height)
    {
        Width = width;
        Height = height;
        CountOfInstances++;
    }
    public int Width { get; set; }
    public int Height { get; set; }
}
```



# [[Single Responsability Principle]]
One of the [SOLID](0-SOLID) Principles
# NameSpaces
Logical arrangement of files
We can put classes, interfaces, etc on a namespace that say about what we are doing in there
Using folders, projects, etc
# Global Using Directives
We can use a directive NameSpace globaly
To do it we have to import using global, and has to be before the comum usings
```C$
global using System.Diagnostics;
using XPTO
```
## How to measure application time
We can use System.Diagnostics to do it
```C#
using System.Diagnostics;

var stopWatch = Stopwatch.StartNew();
for(int i = 0; i < 1000; i++) {
    Console.WriteLine(i);
}
stopWatch.Stop();
Console.WriteLine($"Time in ms: {stopWatch.ElapsedMilliseconds}");
```
# Magic Number Antipattern
When we pass a number and dont identifie why we are using this number
For example, in a dice, we have six sides, but using Random() we have to pass the side value plus one
And if someday it changes, we will have to make changes on intere project
```C#
var random = new Random();
var value = random.Next(1,7); //this is consideretad a antipatter
```
To avoid that, we can use const and variables to be more specific
```C#
const int Sides = 6;
var random = new Random();
var value = random.Next(1,Sides + 1); 
```