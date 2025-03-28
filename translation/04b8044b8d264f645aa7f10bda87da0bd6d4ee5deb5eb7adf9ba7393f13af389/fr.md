```
values(a::AbstractDict)
```

Renvoie un itérateur sur toutes les valeurs d'une collection. `collect(values(a))` renvoie un tableau de valeurs. Lorsque les valeurs sont stockées en interne dans une table de hachage, comme c'est le cas pour `Dict`, l'ordre dans lequel elles sont renvoyées peut varier. Mais `keys(a)`, `values(a)` et `pairs(a)` itèrent tous `a` et renvoient les éléments dans le même ordre.

# Exemples

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} avec 2 entrées :
  'a' => 2
  'b' => 3

julia> collect(values(D))
Vecteur{Int64} de 2 éléments :
 2
 3
```
