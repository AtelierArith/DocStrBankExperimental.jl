```
pairs(collection)
```

Renvoie un itérateur sur des paires `clé => valeur` pour toute collection qui associe un ensemble de clés à un ensemble de valeurs. Cela inclut les tableaux, où les clés sont les indices du tableau. Lorsque les entrées sont stockées en interne dans une table de hachage, comme c'est le cas pour `Dict`, l'ordre dans lequel elles sont renvoyées peut varier. Mais `keys(a)`, `values(a)` et `pairs(a)` itèrent tous `a` et renvoient les éléments dans le même ordre.

# Exemples

```jldoctest
julia> a = Dict(zip(["a", "b", "c"], [1, 2, 3]))
Dict{String, Int64} avec 3 entrées :
  "c" => 3
  "b" => 2
  "a" => 1

julia> pairs(a)
Dict{String, Int64} avec 3 entrées :
  "c" => 3
  "b" => 2
  "a" => 1

julia> foreach(println, pairs(["a", "b", "c"]))
1 => "a"
2 => "b"
3 => "c"

julia> (;a=1, b=2, c=3) |> pairs |> collect
Vecteur de 3 éléments{Pair{Symbol, Int64}} :
 :a => 1
 :b => 2
 :c => 3

julia> (;a=1, b=2, c=3) |> collect
Vecteur de 3 éléments{Int64} :
 1
 2
 3
```
