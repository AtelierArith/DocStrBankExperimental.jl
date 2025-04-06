```
-(x)
```

Operador unario menos.

Véase también: [`abs`](@ref), [`flipsign`](@ref).

# Ejemplos

```jldoctest
julia> -1
-1

julia> -(2)
-2

julia> -[1 2; 3 4]
2×2 Matrix{Int64}:
 -1  -2
 -3  -4

julia> -(true)  # se promueve a Int
-1

julia> -(0x003)
0xfffd
```
