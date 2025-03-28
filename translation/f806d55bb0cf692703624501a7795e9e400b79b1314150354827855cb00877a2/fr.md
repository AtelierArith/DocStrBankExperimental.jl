```
replace(A, old_new::Pair...; [count::Integer])
```

Renvoie une copie de la collection `A` où, pour chaque paire `old=>new` dans `old_new`, toutes les occurrences de `old` sont remplacées par `new`. L'égalité est déterminée en utilisant [`isequal`](@ref). Si `count` est spécifié, alors remplace au maximum `count` occurrences au total.

Le type d'élément du résultat est choisi en utilisant la promotion (voir [`promote_type`](@ref)) en fonction du type d'élément de `A` et des types des valeurs `new` dans les paires. Si `count` est omis et que le type d'élément de `A` est un `Union`, le type d'élément du résultat n'inclura pas les types singleton qui sont remplacés par des valeurs d'un type différent : par exemple, `Union{T,Missing}` deviendra `T` si `missing` est remplacé.

Voir aussi [`replace!`](@ref), [`splice!`](@ref), [`delete!`](@ref), [`insert!`](@ref).

!!! compat "Julia 1.7"
    La version 1.7 est requise pour remplacer des éléments d'un `Tuple`.


# Exemples

```jldoctest
julia> replace([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace([1, missing], missing=>0)
2-element Vector{Int64}:
 1
 0
```
