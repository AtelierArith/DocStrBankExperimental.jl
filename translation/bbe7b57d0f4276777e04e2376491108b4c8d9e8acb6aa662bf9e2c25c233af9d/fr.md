```
isdisjoint(x)
```

Créez une fonction qui compare son argument à `x` en utilisant [`isdisjoint`](@ref), c'est-à-dire une fonction équivalente à `y -> isdisjoint(y, x)`. La fonction retournée est de type `Base.Fix2{typeof(isdisjoint)}`, qui peut être utilisée pour implémenter des méthodes spécialisées.

!!! compat "Julia 1.11"
    Cette fonctionnalité nécessite au moins Julia 1.11.

