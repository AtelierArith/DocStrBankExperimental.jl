```
occursin(haystack)
```

Créez une fonction qui vérifie si son argument se trouve dans `haystack`, c'est-à-dire une fonction équivalente à `needle -> occursin(needle, haystack)`.

La fonction retournée est de type `Base.Fix2{typeof(occursin)}`.

!!! compat "Julia 1.6"
    Cette méthode nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> search_f = occursin("JuliaLang est un langage de programmation");

julia> search_f("JuliaLang")
true

julia> search_f("Python")
false
```
