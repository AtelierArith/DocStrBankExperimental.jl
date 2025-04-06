```
typemax(T)
```

La valeur la plus élevée représentable par le `DataType` numérique (réel) donné.

Voir aussi : [`floatmax`](@ref), [`typemin`](@ref), [`eps`](@ref).

# Exemples

```jldoctest
julia> typemax(Int8)
127

julia> typemax(UInt32)
0xffffffff

julia> typemax(Float64)
Inf

julia> typemax(Float32)
Inf32

julia> floatmax(Float32)  # plus grand nombre à virgule flottante Finie Float32
3.4028235f38
```
