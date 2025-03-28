```
copy(A::Transpose)
copy(A::Adjoint)
```

Bewerten Sie die faule Matrixtransposition/-adjungierung eifrig. Beachten Sie, dass die Transposition rekursiv auf die Elemente angewendet wird.

Dieser Vorgang ist für die Verwendung in der linearen Algebra gedacht - für allgemeine Datenmanipulation siehe [`permutedims`](@ref Base.permutedims), das nicht rekursiv ist.

# Beispiele

```jldoctest
julia> A = [1 2im; -3im 4]
2×2 Matrix{Complex{Int64}}:
 1+0im  0+2im
 0-3im  4+0im

julia> T = transpose(A)
2×2 transpose(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 1+0im  0-3im
 0+2im  4+0im

julia> copy(T)
2×2 Matrix{Complex{Int64}}:
 1+0im  0-3im
 0+2im  4+0im
```
