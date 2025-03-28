```
indexin(a, b)
```

Renvoie un tableau contenant le premier index dans `b` pour chaque valeur dans `a` qui est membre de `b`. Le tableau de sortie contient `nothing` partout où `a` n'est pas membre de `b`.

Voir aussi : [`sortperm`](@ref), [`findfirst`](@ref).

# Exemples

```jldoctest
julia> a = ['a', 'b', 'c', 'b', 'd', 'a'];

julia> b = ['a', 'b', 'c'];

julia> indexin(a, b)
6-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
 2
  nothing
 1

julia> indexin(b, a)
3-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
```
