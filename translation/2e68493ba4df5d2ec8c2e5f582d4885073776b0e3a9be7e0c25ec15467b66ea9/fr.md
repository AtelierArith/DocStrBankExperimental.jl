```
getindex(collection, key...)
```

Récupère la ou les valeurs stockées à la clé ou à l'index donné dans une collection. La syntaxe `a[i,j,...]` est convertie par le compilateur en `getindex(a, i, j, ...)`.

Voir aussi [`get`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# Exemples

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} avec 2 entrées :
  "b" => 2
  "a" => 1

julia> getindex(A, "a")
1
```
