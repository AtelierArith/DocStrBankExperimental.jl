```
unique(f, itr)
```

Renvoie un tableau contenant une valeur de `itr` pour chaque valeur unique produite par `f` appliqué aux éléments de `itr`.

# Exemples

```jldoctest
julia> unique(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4
```

Cette fonctionnalité peut également être utilisée pour extraire les *indices* des premières occurrences d'éléments uniques dans un tableau :

```jldoctest
julia> a = [3.1, 4.2, 5.3, 3.1, 3.1, 3.1, 4.2, 1.7];

julia> i = unique(i -> a[i], eachindex(a))
4-element Vector{Int64}:
 1
 2
 3
 8

julia> a[i]
4-element Vector{Float64}:
 3.1
 4.2
 5.3
 1.7

julia> a[i] == unique(a)
true
```
