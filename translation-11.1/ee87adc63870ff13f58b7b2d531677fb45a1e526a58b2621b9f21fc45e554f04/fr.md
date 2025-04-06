```
replace!(A, old_new::Pair...; [count::Integer])
```

Pour chaque paire `old=>new` dans `old_new`, remplacez toutes les occurrences de `old` dans la collection `A` par `new`. L'égalité est déterminée en utilisant [`isequal`](@ref). Si `count` est spécifié, alors remplacez au maximum `count` occurrences au total. Voir aussi [`replace`](@ref replace(A, old_new::Pair...)).

# Exemples

```jldoctest
julia> replace!([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace!(Set([1, 2, 3]), 1=>0)
Set{Int64} with 3 elements:
  0
  2
  3
```
