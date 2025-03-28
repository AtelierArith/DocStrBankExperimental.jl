```
startswith(prefix)
```

Créez une fonction qui vérifie si son argument commence par `prefix`, c'est-à-dire une fonction équivalente à `y -> startswith(y, prefix)`.

La fonction retournée est de type `Base.Fix2{typeof(startswith)}`, qui peut être utilisée pour implémenter des méthodes spécialisées.

!!! compat "Julia 1.5"
    L'argument unique `startswith(prefix)` nécessite au moins Julia 1.5.


# Exemples

```jldoctest
julia> startswith("Julia")("JuliaLang")
true

julia> startswith("Julia")("Ends with Julia")
false
```
