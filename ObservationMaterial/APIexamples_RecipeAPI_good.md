# MyBakery Platform

## Recipe API

### `addStep(string, int, Step)` method

### Usage

`recipe.addStep(position, stepNbr, newStep)`

The method calls on the `Recipe` class to add a new `Step`<sup><cite>[Spec][1]</cite></sup>.

### Parameters

|Name | Type | Description |
|---------|--------|-------------|
|`position`| string | Specifies if the step should be added before or after `stepNbr`. Acceptable inputs are `'after'`, `'before'` |
|`stepNbr`| int | Takes a positive int. Specifies the number of the new step. If the number is larger than the last step in the `Recipe`, the step will be added last. |
|`newStep`| Step | The new step to be added. See Step<sup><cite>[Spec][1]</cite></sup>.

### Returns

|Return type | Status | Description |
|---------|--------|-------------|
|`void`| Success | On success, the function will not return anything|
|`WrongParametersError`| Error | This error is returned when the parameters are of the wrong format. |
|`NotEnoughArumentsError` | Error | This error will be returned when there are not enough arguments. |

### Examples

This example makes a strawberry cake, but adds a pause step after step 4.
```
let recipeDB = new RecipeDatabase('recipes/cakes.json');
let recipe = recipeDB.getRecipe('strawberry cake');
recipe.addStep('after', 4, new Step('pause', 300000));
```


[1]: #