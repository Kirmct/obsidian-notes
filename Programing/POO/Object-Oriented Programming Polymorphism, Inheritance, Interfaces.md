# Polymorphism
Is the provision of a single interface to entities of differente types.

There is a generic concept of something (Ingredient), and this concept can be made concrete by multiple types (Cheddar, Mozzarella). All of them can be used wherever the generic concept is needed (in the Ingredients list).

# Inheritance
Is a way that we can do polymorphism.
Enable us to create new classes that reuse, extend, and modify the behavior defined in the other classes.

The class whose members are inherited is called the *base class*, and the class that inherits those members is called the derived class.

# Protected access modifier
Share commom logic and data
Public methods and filds always can be used
Private methods and filds only can be used in the base class
Protect methods and filds and properties can be used by the base class and classes that inherits the base class
# Overriding
GeneralTyp variable = new SpecificType()
variable.SomeMethod();
Is virtual?
if yes
	check the actual type of the object stored in the variable
	use SomeMethod from this type if it overrides the base type method
if not
	use SomeMethod from GeneralType
## Virtual
Methods or properties may be overridden by the inheriting types

```C#
public class Ingredient 
{
    public virtual string Name => "Some Ingredient";
}

public class Tomato : Ingredient
{
    public override string Name => "Tomato";
}
```
Ex2:
```C#
namespace POO.Exercise;

public class StringsProcessorEx
{
    public List<string> ProcessAll(List<string> words)
    {
        var stringsProcessors = new List<StringsProcessor>
                {
                    new StringsTrimmingProcessor(),
                    new StringsUppercaseProcessor()
                };

        List<string> result = words;
        foreach (var stringsProcessor in stringsProcessors)
        {
            result = stringsProcessor.Process(result);
        }
        return result;
    }

    public class StringsProcessor
    {
        public virtual List<string> Process(List<string> input, bool? isToHalf = false, bool? isToUpper = false)
        {
            var result = new List<string>();
            foreach (var item in input)
            {
                if(isToHalf != null && isToHalf.Value)
                {
                    result.Add(item.Substring(0, item.Length / 2));
                    continue;
                }

                if(isToUpper != null && isToUpper.Value)
                {
                    result.Add(item.ToUpper());
                    continue;
                }
                result.Add(item);
            }
            return result;
        }
    }
    public class StringsTrimmingProcessor : StringsProcessor
    {
        public override List<string> Process(List<string> input, bool? isToHalf = false, bool? isToUpper = false)
        {
            return base.Process(input: input, isToHalf = true);
        }
    }
    public class StringsUppercaseProcessor : StringsProcessor
    {
        public override List<string> Process(List<string> input, bool? isToHalf = false, bool? isToUpper = false)
        {
            return base.Process(input: input, isToUpper: true);
        }
    }
}

```
# Inheriting constructors and the Base keyword
we can use the Base keyword to pass arguments into constructors
# Implicit conversion
Doesnt require cast expression
Is done when the conversio is safe and lossless\
```C#
int integer = 10;
decimal b = integer;
```
# Explicit conversion
```C#
decimal c = 10.01m;
int d = (int)c;
```

# Upcasting and Downcasting
Upcasting: is when we convert a derived class into a base class
```C#
Ingredient ingredient = new Cheddar();
```
Cheddar always be an igredient
Downcasting: happens when we assign a base class into a derived class
```C#
Cheddar cheddar = (Cheddar)ingredient;
```
Ingredient can be something else, not only cheddar
Can be risk
Possible when we use downcasting the code has design problem
# Is operator

Checks if some object is of a given type
```C#
string word = "hello";
bool isString = word is string;
bool isInt = word is int;
```
one kind of short sintaxe
```C#
if(randomIngredient is Cheddar cheddar)//here we create a variable called cheddar
	Console.WriteLine(cheddar);
```
# Null
Values of fields are initialized with the base value of their types;
Null means that a field or variable has not value, doesnt have a instance;
Commun for all classes;
NullReference excpetion -> when we try to access a member of a null object
# As operator
We can use As operator instead a downcasting
```C#
Cheddar cheddar = ingredient as Cheddar;
```
It will cause an exception if cast fails if we use casting
Using as operator will give null, if the cast fails;
We only can use as with a nullable type, an int, exemple, cant be used, cause int dont acept null values;
# Absctract classes
Are classes that cant be intanciated. Only serve as a base classes for others, can only be inherited.
# Abstract methods
Remember what are virtual methods
-> Methods that may be overridden in the derived classes
They can only be defined in abstract classes
They dont have implementations
```C#
public abstract class Ingredient 
{
    public virtual string Name => "Some Ingredient";
    //all abstract methods are implicitly virtual
    //must be overriden in non abstract derived classes
    public abstract void Prepare();
}

public class Tomato : Ingredient
{
    public override string Name => "Tomato";

    public override void Prepare()
    {
        //something
    }
}
```
# A need for abstracts methods
Polymorphism
Dont provide any implementation
All the derived types must proveide their own implementation
Implicitly virtual
# Sealed Classes and Methods
Used when we dont want that the class or method can be inherited;
Only virtual overridden methods can be sealed
# Static Classes are Always Sealed
Static classes are implicitly sealed;
We cant derive from them;
# Extension Methods
Allow us to seemingly add mthods to an existing type without modifying this types source code.
```C#
public static class StringExtensions
{
	publis static int CountLines(this string input) =>   
		input.Split(Environment.NewLine).Length;
}
```
# Interfaces
Used to define a base type for types exposing methods with the same signature
Inheritance creates an 'is-a' kind of relationship between types
INTERFACES -> create a 'behaves-like' kind
Interfaces define contracts, all types that use this interface has to implement this signature;
All methods into a interface has to be public, also implicitly virtual
Cant be initialized
# Interfaces x Abstract Classes
INTERFACE:
	Defines the set of operations that the implementing type must provide
	Does not provide any implementation on its on
	Does not contain any data
	Abstraction over: behavior
	Defines what an object: can do
	Group of types share: behavior
	Not sure what it: is
	Sure what it: is able to do
	Part of speech: verb
ABSTRACT CLASS:
	Its like a general grouping for derived classes
	Blueprint for derived classes, representing a general category of things
	May provide implementations in non-abstract methods. Can also have abstract methods
	Can contain data
	Abstraction over: alikeness
	Defines what an object: is
	Group of types share: general category of things
	Not sure what it: is able to do
	Sure what it: is
	Part of speech: noun

# JSON and XML
Kinds of store data as a string
```C#
var person = new Person 
{
    FirstName = "Kirmct",
    LastName  = "Neto",
    YearOfBirth = 1998
};

var asJson = JsonSerializer.Serialize(person);

var personAsJson = JsonSerializer.Deserialize<Person>("OBJECT HERE");

public class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int YearOfBirth { get; set; }
}
```
