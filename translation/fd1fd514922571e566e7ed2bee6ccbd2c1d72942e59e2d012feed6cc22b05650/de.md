```
typemax(T)
```

Der höchste Wert, der durch den gegebenen (reellen) numerischen `DataType` darstellbar ist.

Siehe auch: [`floatmax`](@ref), [`typemin`](@ref), [`eps`](@ref).

# Beispiele

```jldoctest
julia> typemax(Int8)
127

julia> typemax(UInt32)
0xffffffff

julia> typemax(Float64)
Inf

julia> typemax(Float32)
Inf32

julia> floatmax(Float32)  # größter endlicher Float32-Gleitkommawert
3.4028235f38
```
