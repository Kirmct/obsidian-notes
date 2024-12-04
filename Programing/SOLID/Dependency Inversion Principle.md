The dependency inversion principle states that high-level modules should not depend on low-level modules, both should depend on abstractions;
The dependencies of a type, should not be concretl they should be abstractions;
In C# abstractions means use interfaces to make contracts to be follow
```C#
private readonly IRecipesConsoleUserInteraction _recipesConsoleUserInteraction =
	new RecipesConsoleUserInteraction();
	//this is a bad way, coupling is to high at this aproach
```
We can use this aproach:
We gonna inject the argument using the constructor, this way is called dependency injection
```C#
private readonly IRecipesConsoleUserInteraction _recipesConsoleUserInteraction;

public CookiesRecipesApp(
     IRecipesConsoleUserInteraction recipesUserInteraction)
 {
     _recipesConsoleUserInteraction = recipesUserInteraction;
 }
```

# Dependency Inversion
Is a principle saying that types should depend on abstractions, not on concrete types

# Dependency Injection
Means the class is given the dependencies it needs, it doesnt create them itself

# Coupling
We can create parameters inside the classes, but if we use constructor we get more flexibiliity;
Is the degree of interdenpendence between classes, a measure of how closely they are connected
Should be avoided
Less reasuble
