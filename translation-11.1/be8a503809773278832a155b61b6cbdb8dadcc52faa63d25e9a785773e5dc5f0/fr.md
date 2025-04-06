```
promote_type(type1, type2, ...)
```

La promotion fait référence à la conversion de valeurs de types mixtes en un type commun unique. `promote_type` représente le comportement de promotion par défaut dans Julia lorsque des opérateurs (généralement mathématiques) reçoivent des arguments de types différents. `promote_type` essaie généralement de renvoyer un type qui peut au moins approcher la plupart des valeurs de l'un ou l'autre type d'entrée sans élargir excessivement. Une certaine perte est tolérée ; par exemple, `promote_type(Int64, Float64)` renvoie [`Float64`](@ref) même si, strictement, toutes les valeurs [`Int64`](@ref) ne peuvent pas être représentées exactement comme des valeurs [`Float64`](@ref).

Voir aussi : [`promote`](@ref), [`promote_typejoin`](@ref), [`promote_rule`](@ref).

# Exemples

```jldoctest
julia> promote_type(Int64, Float64)
Float64

julia> promote_type(Int32, Int64)
Int64

julia> promote_type(Float32, BigInt)
BigFloat

julia> promote_type(Int16, Float16)
Float16

julia> promote_type(Int64, Float16)
Float16

julia> promote_type(Int8, UInt16)
UInt16
```

!!! warning "Ne surchargez pas cela directement"
    Pour surcharger la promotion pour vos propres types, vous devez surcharger [`promote_rule`](@ref). `promote_type` appelle `promote_rule` en interne pour déterminer le type. Surcharger `promote_type` directement peut entraîner des erreurs d'ambiguïté.

