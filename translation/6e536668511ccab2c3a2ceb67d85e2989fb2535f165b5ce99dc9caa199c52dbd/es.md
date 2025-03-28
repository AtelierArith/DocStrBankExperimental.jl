```
diagind(M::AbstractMatrix, k::Integer = 0, indstyle::IndexStyle = IndexLinear())
diagind(M::AbstractMatrix, indstyle::IndexStyle = IndexLinear())
```

Un `AbstractRange` que da los índices de la `k`-ésima diagonal de la matriz `M`. Opcionalmente, se puede especificar un estilo de índice que determina el tipo de rango devuelto. Si `indstyle isa IndexLinear` (por defecto), esto devuelve un `AbstractRange{Integer}`. Por otro lado, si `indstyle isa IndexCartesian`, esto devuelve un `AbstractRange{CartesianIndex{2}}`.

Si `k` no se proporciona, se asume que es `0` (correspondiente a la diagonal principal).

Ver también: [`diag`](@ref), [`diagm`](@ref), [`Diagonal`](@ref).

# Ejemplos

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diagind(A, -1)
2:4:6

julia> diagind(A, IndexCartesian())
StepRangeLen(CartesianIndex(1, 1), CartesianIndex(1, 1), 3)
```

!!! compat "Julia 1.11"
    Especificar un `IndexStyle` requiere al menos Julia 1.11.

