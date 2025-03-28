```
typemin(T)
```

La plus basse valeur représentable par le type de données numériques (réel) donné `T`.

Voir aussi : [`floatmin`](@ref), [`typemax`](@ref), [`eps`](@ref).

# Exemples

```jldoctest
julia> typemin(Int8)
-128

julia> typemin(UInt32)
0x00000000

julia> typemin(Float16)
-Inf16

julia> typemin(Float32)
-Inf32

julia> nextfloat(-Inf32)  # plus petit nombre à virgule flottante Float32 fini
-3.4028235f38
```
