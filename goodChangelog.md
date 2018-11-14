# Change Log to MyBakery API

## Version 5.3
7 November 2018

We are happy to announced that this latest release introduces our new, 
more efficient, `SuperCakeMachineEngine` that addresses many of the issues the
community have pointed about. This release sees new methods, updated methods, deprecated methods 
and bug fixes. We also talk about known bugs that we are still working on.

### New Methods

With the release we present two new methods.

#### `createSuperEngine()`

This is the new method to create the cake engine. It replaces the now deprecated `createEngine()`

 Read specifications here: **<cite>[createSuperEngine specifications][1]</cite>**
 
 ----

#### `makeAnySizeCake(int: size)`

This method replaces the methods `makeLargeCake()`, `makeMediumCake()` and `makeSmallCake`.

 Read specifications here: **<cite>[makeAnySizeCake spec][1]</cite>**


### Updated Methods

`serveCake(string: place)` now also supports the input `inFace`.
 
 Read specifications here: **<cite>[serveCake spec][1]</cite>**

### Deprecated Methods
Some methods will be deprecated with the this release. 

#### List of depricated methods
* `createEngine()`, instead use `createSuperEngine()`

`createEngine()` will not be supported with the introduction of our new engine.

* `makeLargeCake()`, instead use `makeAnySizeCake(500)`
* `makeMediumCake()`, instead use `makeAnySizeCake(300)`
* `makeSmallCake()`, instead use `makeAnySizeCake(100)`

The reasoning behind removing the  methods are that they are reliant on our old `BadCakeMachineEnginge`
that had performance issues. With the introduction of `makeAnySizeCake`, the baker can make any sized cake.

* `makeHorribleCake()`

This method has been deprecated since it's usage has been close to zero. If you still wish to use it
the following code will yield the same result:
```
let engine = createSuperEngine();
let baker = new Baker(engine);
baker.setRecipe('weddingCake');
baker.getIngredients().forEach((ingredient) => {
   ingredient.setAmount('random');
});
baker.makeCake();
```
### Bug fixes

#### The egg bug

The method `addEggs(float: amount)` had a bug where you could only add even amount of eggs.
This was due to a bug in the `Baker` class where it used the `mainBowl` class
instead `separateBowl` and then retrieving the correct amount. This has now been fixed.

The bug was introduced in version 5.0. Read more about the release here: <cite>[5.0 - A Better Baker!][1]</cite>

#### The overheating bug

The method `setSpeed(int: speed)` had an issue where setting a speed to over 9000 would overheat
the engine. This was due to a bug in the old engine where `extremeCoolingSystem` was not set to `true`.
This has now been fixed.

The bug was introduced in version 5.2. Read more about that release here: <cite>[Version 5.2 - Power savings][1]</cite>

### Known bugs

#### BakerPropertyError

We are currently still working on the bug of the baker returning the error code of:

```
BakerPropertyError: {
    Name: John Smith
    Age: 54
    State: HungOver
    EnergyLevel: -1
}
Expected EnergyLevel to be 100.
Could not bake cake.
```

The bug has existed since <cite>[Version 5.0 - A Better Baker!][1]</cite> and occurs when using the method `setDay('sunday')`.
 We recommend not using this method in production at the moment.
 
 We have made a blog post on a workaround for this issue that you can read about here: <cite>[BakerPropertyError: 
 A workaround with Baker.enforce('sobriety') ][1]</cite>

The bug is still not solved, but we are working on it and hope to fix it shortly.

[1]: #