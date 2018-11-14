# MyBakery API

## Baker

### `makeCake()`

`makeCake(Engine)` follows the exact instructions and amounts given by `Recipe`<sup><cite>[Spec][1]</cite></sup>. It will automatically change `mode` 
of `Engine`<sup><cite>[Spec][1]</cite></sup>. It returns an object of the class `Cake`<sup><cite>[Spec][1]</cite></sup>.

#### Returns

|Return type | Status | Description |
|---------|--------|-------------|
|`Cake`| Success | On success, the function will return an object of the class `Cake` |
|`NoEngineError`| Error | This error is returned when either `Baker` has not been assigned an `Engine` or the assigned `Engine` is busy|
|`LowEnergyError` |Error | This error is returned when the `Baker` class has less energy than required by the `Recipe`
|`WrongEngineModeError`| Error| This error is returned when the mode of the `Engine` `mode` does not match the mode required by `Recipe` | 


#### Example

##### Simple Example
This example makes a strawberry cake without any changes.
```
let engine = makeSuperEngine();
let baker = new Baker(engine);
baker.setRecipe('strawberry cake');
let cake = baker.makeCake();
baker.serveCake(cake);
```
##### Advanced Example
This example makes a strawberry cake, but doubles the amount of flour, changes the speed of the engine 
and adds a pause step after step 4.
```
let engine = makeSuperEngine();
let baker = new Baker(engine);
baker.setRecipe('strawberry cake');
baker.setIngredientAmount(baker.getIngredient('flour').changeAmount(2));
baker.getEngine().setSpeed(400);
baker.getRecipe().addStep('after', 4, new Step('pause', 300000));
baker.makeCake();
```


[1]: #