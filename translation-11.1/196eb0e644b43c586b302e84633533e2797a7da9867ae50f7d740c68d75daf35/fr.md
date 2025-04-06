```
isbitstype(T)
```

Retourne `true` si le type `T` est un type de "données simples", ce qui signifie qu'il est immuable et ne contient aucune référence à d'autres valeurs, seulement des types `primitifs` et d'autres types `isbitstype`. Des exemples typiques sont les types numériques tels que [`UInt8`](@ref), [`Float64`](@ref) et [`Complex{Float64}`](@ref). Cette catégorie de types est significative car elle est valide en tant que paramètres de type, peut ne pas suivre l'état [`isdefined`](@ref) / [`isassigned`](@ref), et a une disposition définie qui est compatible avec C. Si `T` n'est pas un type, alors retourne `false`.

Voir aussi [`isbits`](@ref), [`isprimitivetype`](@ref), [`ismutable`](@ref).

# Exemples

```jldoctest
julia> isbitstype(Complex{Float64})
true

julia> isbitstype(Complex)
false
```
