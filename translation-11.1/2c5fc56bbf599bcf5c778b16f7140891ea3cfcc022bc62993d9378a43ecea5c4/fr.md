```
delete!(collection, key)
```

Supprime la correspondance pour la clé donnée dans une collection, le cas échéant, et renvoie la collection.

# Exemples

```jldoctest
julia> d = Dict("a"=>1, "b"=>2)
Dict{String, Int64} avec 2 entrées :
  "b" => 2
  "a" => 1

julia> delete!(d, "b")
Dict{String, Int64} avec 1 entrée :
  "a" => 1

julia> delete!(d, "b") # d reste inchangé
Dict{String, Int64} avec 1 entrée :
  "a" => 1
```
