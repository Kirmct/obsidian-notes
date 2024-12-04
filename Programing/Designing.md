An aproach to make good designer is first use classes to think about the implementation
Designing a good interface fr a calss is much harder, but also much more important tha making all the implementation details right.

We create the high level design, based on logic to create step by step the app, but we dont considere the implementation:
```C#
using CookBook.DataAccess.Repositories;
using CookBook.Models;

var cookiesRecipesApp = new CookiesRecipesApp();
cookiesRecipesApp.Run();

public class CookiesRecipesApp
{
    private readonly RecipesRepository _recipesRepository;
    private readonly RecipesUserInteraction _recipesUserInteraction;

    public CookiesRecipesApp(
        RecipesRepository recipesRepository, 
        RecipesUserInteraction recipesUserInteraction)
    {
        _recipesRepository = recipesRepository;
        _recipesUserInteraction = recipesUserInteraction;
    }

    public void Run()
    {
        var allRecipes = _recipesRepository.Read(filePath);
        _recipesUserInteraction.PrintExistingRecipes(allRecipes);

        _recipesUserInteraction.PromptToCreateRecipe();

        var ingredients = _recipesUserInteraction.ReadIngredientsFromUser();

        if (ingredients.Count > 0)
        {
            var recipe = new Recipe(ingredients);
            allRecipes.Add(recipe);
            _recipesRepository.Write(filePath, allRecipes);

            _recipesUserInteraction.ShowMessage("Recipe added: ");
            _recipesRepository.ShowMessage(recipe.ToString());
        }
        else 
        {
            _recipesUserInteraction.ShowMessage(
                "No ingredients have been selected. " +
                "Recipe will not be saved.");
        }

        _recipesUserInteraction.Exit();
    }
}
```
This example was created only thinking about the usability, not the implementation, all this classes are not created yet, but what we want to do was think using this classes to help us