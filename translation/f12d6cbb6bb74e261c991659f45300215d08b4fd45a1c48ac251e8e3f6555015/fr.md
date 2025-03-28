```
setindex!(collection, value, key...)
```

Stockez la valeur donnée à la clé ou à l'index donné dans une collection. La syntaxe `a[i,j,...] = x` est convertie par le compilateur en `(setindex!(a, x, i, j, ...); x)`.

# Exemples

```jldoctest
julia> a = Dict("a"=>1)
Dict{String, Int64} avec 1 entrée :
  "a" => 1

julia> setindex!(a, 2, "b")
Dict{String, Int64} avec 2 entrées :
  "b" => 2
  "a" => 1
```
