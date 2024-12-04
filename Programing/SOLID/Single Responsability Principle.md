One of the most important principles in programming
A class should be responsible for only one thing
Shoule have only on reason to change
Bad Example:
```C#
public class Names
{
    private List<string> _names = [];
    public void AddName(string name)
    {
        if(IsValidName(name))
            _names.Add(name);
    }

    private bool IsValidName(string name)
    {
        return name.Length >= 2 &&
            name.Length < 35 &&
            char.IsUpper(name[0]) &&
            name.All(char.IsLetter);
    }

    public void ReadFromTextFile()
    {
        var fileContents = File.ReadAllText(BuildfilePath());
        var namesFromFile = fileContents.Split(Environment.NewLine).ToList();
        foreach (var name in namesFromFile)
        {
            AddName(name);
        }
    }

    public void WriteToTextFile() {
        File.WriteAllText(BuildfilePath(), Format());
    }

    public string BuildfilePath()
    {
        //can be more complicated
        //like provided by the user and validated
        return "names.txt";
    }

    public string Format()
    {
        return string.Join(Environment.NewLine, _names);
    }
}
```
This class has many responsabilities, 5 at least
	Works as a container for names
	Also knows how a name can be validated
	Responsable to reading and write a text file
	And building a file path
	And how to format a list of name

## Repositories 
Are classes or components that encapsulate the logic required to access data sources

Refactoring the classe before we have:
```C#
public class NamesValidator 
{
    public bool IsValid(string name)
    {
        return name.Length >= 2 &&
            name.Length < 35 &&
            char.IsUpper(name[0]) &&
            name.All(char.IsLetter);
    }
}

public class StringsTextualRepository 
{
    private static readonly string Separator = Environment.NewLine;
    public List<string> Read(string filePath)
    {
        var fileContents = File.ReadAllText(filePath);
        return fileContents.Split(Separator).ToList();       
    }
    //notice that the two methods work similiar, using Envoriment.NewLine and a List<string>
    public void Write(string filePath, List<string> strings)
    {
        File.WriteAllText(filePath, string.Join(Separator, strings));
    }
}

public class Names
{
    public List<string> All { get; } = [];
    private readonly NamesValidator _namesValidators = new NamesValidator();

    public void AddNames(List<string> stringsFromFile)
    {
        foreach (var name in stringsFromFile) 
            AddName(name);        
    }

    public void AddName(string name)
    {
        if(_namesValidators.IsValid(name))
            All.Add(name);
    }      

    public string BuildfilePath()
    {
        //can be more complicated
        //like provided by the user and validated
        return "names.txt";
    }

    public string Format()
    {
        return string.Join(Environment.NewLine, All);
    }
}
```

## DRY Principle - Dont Repeat Yourself
Many people think the DRY principle means "dont repeat any code; extract methods and reuse them instead"
Not acurate, he says
DRY states that we shouldnt have multiple places in the code where the same business decisions are defined
We can have the similar code, if theyr responsabilites are other, like in the Format() and Write() methods, use the same code but in the future one of them can change, not necessary the other has to change too
```C#
public class NamesValidator 
{
    public bool IsValid(string name)
    {
        return name.Length >= 2 &&
            name.Length < 35 &&
            char.IsUpper(name[0]) &&
            name.All(char.IsLetter);
    }
}

public class StringsTextualRepository 
{
    private static readonly string Separator = Environment.NewLine;
    public List<string> Read(string filePath)
    {
        var fileContents = File.ReadAllText(filePath);
        return fileContents.Split(Separator).ToList();       
    }
    //notice that the two methods work similiar, using Envoriment.NewLine and a List<string>
    public void Write(string filePath, List<string> strings)
    {
        File.WriteAllText(filePath, string.Join(Separator, strings));
    }
}

public class StringsBuildFilePath 
{
    public string BuildfilePath()
    {
        //can be more complicated
        //like provided by the user and validated
        return "names.txt";
    }
}

public class NamesFormatter
{
    public string Format(List<string> names)
    {
        return string.Join(Environment.NewLine, names);
    }
}

public class Names
{
    public List<string> All { get; } = [];
    private readonly NamesValidator _namesValidators = new NamesValidator();

    public void AddNames(List<string> stringsFromFile)
    {
        foreach (var name in stringsFromFile) 
            AddName(name);        
    }

    public void AddName(string name)
    {
        if(_namesValidators.IsValid(name))
            All.Add(name);
    }       

}
```

Using this
```C#
using fundamentals;

var names = new Names();
var stringsTextualRepository = new StringsTextualRepository();

var path = new StringsBuildFilePath().BuildfilePath();
if (File.Exists(path))
{
    Console.WriteLine("Name file already exists. Loading names.");
    var stringsFromFile = stringsTextualRepository.Read(path);
    names.AddNames(stringsFromFile);
}
else
{
    Console.WriteLine("Names files doesnt exist yet");

    names.AddName("Kirmct");
    names.AddName("not a valid name");

    Console.WriteLine("Savind names to a file");
    stringsTextualRepository.Write(path, names.All);
}
Console.WriteLine(new NamesFormatter().Format(names.All));
Console.ReadKey();
```