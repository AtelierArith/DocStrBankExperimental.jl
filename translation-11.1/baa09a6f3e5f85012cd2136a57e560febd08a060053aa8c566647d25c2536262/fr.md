```
reinterpret(::Type{Out}, x::In)
```

Changez l'interprétation de type des données binaires dans la valeur isbits `x` à celle du type isbits `Out`. La taille (en ignorant le remplissage) de `Out` doit être la même que celle du type de `x`. Par exemple, `reinterpret(Float32, UInt32(7))` interprète les 4 octets correspondant à `UInt32(7)` comme un [`Float32`](@ref). Notez que `reinterpret(In, reinterpret(Out, x)) === x`

```jldoctest
julia> reinterpret(Float32, UInt32(7))
1.0f-44

julia> reinterpret(NTuple{2, UInt8}, 0x1234)
(0x34, 0x12)

julia> reinterpret(UInt16, (0x34, 0x12))
0x1234

julia> reinterpret(Tuple{UInt16, UInt8}, (0x01, 0x0203))
(0x0301, 0x02)
```

!!! note
    Le traitement du remplissage diffère de reinterpret(::DataType, ::AbstractArray).


!!! warning
    Faites preuve de prudence si certaines combinaisons de bits dans `Out` ne sont pas considérées comme valides et seraient autrement empêchées par les constructeurs et méthodes du type. Un comportement inattendu peut en résulter sans validation supplémentaire.

