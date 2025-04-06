```
getfield(value, name::Symbol, [order::Symbol])
getfield(value, i::Int, [order::Symbol])
```

Extraire un champ d'une valeur composite `value` par nom ou position. En option, un ordre peut être défini pour l'opération. Si le champ a été déclaré `@atomic`, il est fortement recommandé que la spécification soit compatible avec les stockages à cet emplacement. Sinon, s'il n'est pas déclaré comme `@atomic`, ce paramètre doit être `:not_atomic` s'il est spécifié. Voir aussi [`getproperty`](@ref Base.getproperty) et [`fieldnames`](@ref).

# Exemples

```jldoctest
julia> a = 1//2
1//2

julia> getfield(a, :num)
1

julia> a.num
1

julia> getfield(a, 1)
1
```
