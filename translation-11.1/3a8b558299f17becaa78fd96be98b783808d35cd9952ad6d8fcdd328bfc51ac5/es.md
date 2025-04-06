```
repeat(A::AbstractArray; inner=ntuple(Returns(1), ndims(A)), outer=ntuple(Returns(1), ndims(A)))
```

Construye un array repitiendo las entradas de `A`. El i-ésimo elemento de `inner` especifica el número de veces que las entradas individuales de la i-ésima dimensión de `A` deben ser repetidas. El i-ésimo elemento de `outer` especifica el número de veces que una porción a lo largo de la i-ésima dimensión de `A` debe ser repetida. Si se omiten `inner` o `outer`, no se realiza ninguna repetición.

# Ejemplos

```jldoctest
julia> repeat(1:2, inner=2)
4-element Vector{Int64}:
 1
 1
 2
 2

julia> repeat(1:2, outer=2)
4-element Vector{Int64}:
 1
 2
 1
 2

julia> repeat([1 2; 3 4], inner=(2, 1), outer=(1, 3))
4×6 Matrix{Int64}:
 1  2  1  2  1  2
 1  2  1  2  1  2
 3  4  3  4  3  4
 3  4  3  4  3  4
```
