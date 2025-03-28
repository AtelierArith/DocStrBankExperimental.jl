```
get!(collection, key, default)
```

Retourne la valeur stockée pour la clé donnée, ou si aucune correspondance pour la clé n'est présente, stocke `key => default`, et retourne `default`.

# Exemples

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> get!(d, "a", 5)
1

julia> get!(d, "d", 4)
4

julia> d
Dict{String, Int64} avec 4 entrées :
  "c" => 3
  "b" => 2
  "a" => 1
  "d" => 4
```
