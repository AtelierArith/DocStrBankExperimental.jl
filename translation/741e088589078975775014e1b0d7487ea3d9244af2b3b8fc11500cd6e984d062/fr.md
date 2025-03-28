```
endswith(suffix)
```

Créez une fonction qui vérifie si son argument se termine par `suffix`, c'est-à-dire une fonction équivalente à `y -> endswith(y, suffix)`.

La fonction retournée est de type `Base.Fix2{typeof(endswith)}`, qui peut être utilisée pour implémenter des méthodes spécialisées.

!!! compat "Julia 1.5"
    L'argument unique `endswith(suffix)` nécessite au moins Julia 1.5.


# Exemples

```jldoctest
julia> endswith("Julia")("Ends with Julia")
true

julia> endswith("Julia")("JuliaLang")
false
```
