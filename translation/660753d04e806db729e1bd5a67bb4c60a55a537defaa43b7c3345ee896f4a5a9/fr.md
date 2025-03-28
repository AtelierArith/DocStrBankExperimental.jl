```
issetequal(x)
```

Créez une fonction qui compare son argument à `x` en utilisant [`issetequal`](@ref), c'est-à-dire une fonction équivalente à `y -> issetequal(y, x)`. La fonction retournée est de type `Base.Fix2{typeof(issetequal)}`, qui peut être utilisée pour implémenter des méthodes spécialisées.

!!! compat "Julia 1.11"
    Cette fonctionnalité nécessite au moins Julia 1.11.

