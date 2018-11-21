# MyBakery Platform

## Baker API

The `Baker` is the central part of the MyBaker Platform, creating all `Cake` objects.

### `makeCake()` method

### Usage

`baker.makeCake()`

The method calls on the class `Baker` to follow the exact instructions and amounts given by 
`Recipe`<sup><cite>[Spec][1]</cite></sup>. It will automatically 
change `mode` 
of `Engine`<sup><cite>[Spec][1]</cite></sup> if needed. It returns an object of the class 
`Cake`<sup><cite>[Spec][1]</cite></sup> or throws an error.

### Parameters

This method takes no parameters.

### Returns

|Return type | Status | Description |
|---------|--------|-------------|
|`Cake`| Success | On success, the function will return an object of the class `Cake` |
|`NoEngineError`| Error | This error is returned when either `Baker` has not been assigned an `Engine` or the assigned `Engine` is busy|
|`LowEnergyError` |Error | This error is returned when the `Baker` class has less energy than required by the `Recipe`
|`WrongEngineModeError`| Error| This error is returned when the mode of the `Engine` `mode` does not match the mode required by `Recipe` | 


### Examples

#### Example
This example makes a strawberry cake without any changes.
```
let engine = SuperEngine();
let baker = new Baker(engine);
let recipeDB = new RecipeDatabase('recipes/cakes.json');
baker.setRecipe(recipeDB.getRecipe('strawberry cake'));
let cake = baker.makeCake();
baker.serveCake(cake);
```
#### Example with modifications
This example makes a strawberry cake, but doubles the amount of flour, changes the speed of the engine 
and adds a pause step after step 4.
```
let engine = SuperEngine();
let baker = new Baker(engine);
let recipeDB = new RecipeDatabase('recipes/cakes.json');
let recipe = recipeDB.getRecipe('strawberry cake');
recipe.setIngredientAmount('flour', recipe.getAmount('flour')*2);
recipe.addStep('after', 4, new Step('pause', 300000));
baker.setRecipe(recipe);
baker.setEngine(getEngine().setSpeed(400));
let cake = baker.makeCake();
baker.serveCake(cake);
```


[1]: #