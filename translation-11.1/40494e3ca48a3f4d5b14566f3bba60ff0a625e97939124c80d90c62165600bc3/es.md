```
occursin(haystack)
```

Crea una función que verifique si su argumento ocurre en `haystack`, es decir, una función equivalente a `needle -> occursin(needle, haystack)`.

La función devuelta es de tipo `Base.Fix2{typeof(occursin)}`.

!!! compat "Julia 1.6"
    Este método requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> search_f = occursin("JuliaLang is a programming language");

julia> search_f("JuliaLang")
true

julia> search_f("Python")
false
```
