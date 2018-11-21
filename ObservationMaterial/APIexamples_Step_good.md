# MyBakery Platform

## Step

Step is a class used by `Recipe` that describes a step of how to bake a cake. The class has no methods, but is simply
a structure.

## Usage

The class has three different constructors. 

### `new Step(stepName, duration)`
Intended to be used for a standard step without an ingredient. 
If `stepName` already exists in the `RecipeDatabase` the description will be fetched automatically.
### `new Step(stepName, duration, ingredient)`
Intended to be used for a standard step with an ingredient.
### `new Step(stepName, duration, description)`
Intended to be used when adding a custom step that does not exist in the database.

## Parameters

|Name | Type | Description |
|---------|--------|-------------|
|`stepName`| string | Name of the step.
|`duration`| int | Specifies the duration of the step, in milliseconds. Parameter must be a positive int. |
|`ingredient`| string | The name of the ingredient
|`description`| string | Specifies what to do in the step.

### Standard Step Names

These are the standard step names and their respective descriptions.

|Step Name | Description |
|----------|-------------|
|`'pause'`| Pauses all execution for the specified duration. |
|`'mix'`|Mixes the ingredients|
|`'knead'`|Kneads the dough, if it exists|
|`'add'`| Adds the specified ingredient|
|`'repeat'`| Will loop once the steps between `repeat` and `stopRepeat`
|`'stopRepeat'`|Will stop the `repeat` loop.
|`'cool'`| Cools the mixture. |
|`'putInOven'`|Puts the mixture in the oven|
|`'addToSmallPan'`|Adds the mixture to a small pan|
|`'addToBigPan'`| Adds the mixture to a big pan|

## Errors

|Error Type | Description |
|---------|--------|
|`doubleStepNameError`| This error is returned a custom step is trying to be added that already exists in the `RecipeDatabase` |
|`wrongParametersError` | This error will be returned the wrong amount of parameters is put in, the parameters are not of the correct type or the duration is negative. |
|||