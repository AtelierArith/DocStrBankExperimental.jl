```
typemin(T)
```

Der niedrigste darstellbare Wert des angegebenen (reellen) Datentyps `T`.

Siehe auch: [`floatmin`](@ref), [`typemax`](@ref), [`eps`](@ref).

# Beispiele

```jldoctest
julia> typemin(Int8)
-128

julia> typemin(UInt32)
0x00000000

julia> typemin(Float16)
-Inf16

julia> typemin(Float32)
-Inf32

julia> nextfloat(-Inf32)  # kleinste endliche Float32-Gleitkommazahl
-3.4028235f38
```
