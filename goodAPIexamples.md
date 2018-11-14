# MyBakery API

## Baker

### `makeCake()` method

### Usage

`baker.makeCake()`

The method calls on the class `Baker` to follow the exact instructions and amounts given by 
`Recipe`<sup><cite>[Spec][1]</cite></sup>. It will automatically 
change `mode` 
of `Engine`<sup><cite>[Spec][1]</cite></sup> if needed. It returns an object of the class 
`Cake`<sup><cite>[Spec][1]</cite></sup> or throws an error.

#### Parameters

This method takes no parameters.

#### Returns

|Return type | Status | Description |
|---------|--------|-------------|
|`Cake`| Success | On success, the function will return an object of the class `Cake` |
|`NoEngineError`| Error | This error is returned when either `Baker` has not been assigned an `Engine` or the assigned `Engine` is busy|
|`LowEnergyError` |Error | This error is returned when the `Baker` class has less energy than required by the `Recipe`
|`WrongEngineModeError`| Error| This error is returned when the mode of the `Engine` `mode` does not match the mode required by `Recipe` | 


#### Examples

##### Basic Example
This example makes a strawberry cake without any changes.
```
let engine = makeSuperEngine();
let baker = new Baker(engine);
baker.setRecipe('strawberry cake');
let cake = baker.makeCake();
baker.serveCake(cake);
```
##### Example with modifications
This example makes a strawberry cake, but doubles the amount of flour, changes the speed of the engine 
and adds a pause step after step 4.
```
let engine = makeSuperEngine();
let baker = new Baker(engine);
baker.setRecipe('strawberry cake');
baker.setIngredientAmount('flour', baker.getRecipe().getAmount('flour')*2);
baker.getEngine().setSpeed(400);
baker.setRecipe(baker.getRecipe().addStep('after', 4, new Step('pause', 300000));
let cake = baker.makeCake();
baker.serveCake(cake);
```


[1]: #