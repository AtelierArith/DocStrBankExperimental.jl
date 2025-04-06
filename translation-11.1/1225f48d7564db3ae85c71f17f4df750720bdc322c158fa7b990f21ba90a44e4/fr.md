```
isequal(x)
```

Créez une fonction qui compare son argument à `x` en utilisant [`isequal`](@ref), c'est-à-dire une fonction équivalente à `y -> isequal(y, x)`.

La fonction retournée est de type `Base.Fix2{typeof(isequal)}`, qui peut être utilisée pour implémenter des méthodes spécialisées.
