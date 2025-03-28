```
map(f, c...) -> collection
```

Transformez la collection `c` en appliquant `f` à chaque élément. Pour plusieurs arguments de collection, appliquez `f` élément par élément, et arrêtez-vous lorsque l'un d'eux est épuisé.

Voir aussi [`map!`](@ref), [`foreach`](@ref), [`mapreduce`](@ref), [`mapslices`](@ref), [`zip`](@ref), [`Iterators.map`](@ref).

# Exemples

```jldoctest
julia> map(x -> x * 2, [1, 2, 3])
3-element Vector{Int64}:
 2
 4
 6

julia> map(+, [1, 2, 3], [10, 20, 30, 400, 5000])
3-element Vector{Int64}:
 11
 22
 33
```
