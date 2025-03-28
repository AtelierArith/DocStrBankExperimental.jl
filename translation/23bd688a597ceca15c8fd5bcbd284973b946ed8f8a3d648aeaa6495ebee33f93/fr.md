```
isconcretetype(T)
```

Déterminez si le type `T` est un type concret, ce qui signifie qu'il pourrait avoir des instances directes (valeurs `x` telles que `typeof(x) === T`). Notez que ce n'est pas la négation de `isabstracttype(T)`. Si `T` n'est pas un type, alors renvoyez `false`.

Voir aussi : [`isbits`](@ref), [`isabstracttype`](@ref), [`issingletontype`](@ref).

# Exemples

```jldoctest
julia> isconcretetype(Complex)
false

julia> isconcretetype(Complex{Float32})
true

julia> isconcretetype(Vector{Complex})
true

julia> isconcretetype(Vector{Complex{Float32}})
true

julia> isconcretetype(Union{})
false

julia> isconcretetype(Union{Int,String})
false
```
