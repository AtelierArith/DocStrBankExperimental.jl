```
SymTridiagonal(dv::V, ev::V) donde V <: AbstractVector
```

Construye una matriz tridiagonal simétrica a partir de la diagonal (`dv`) y la primera sub/super-diagonal (`ev`), respectivamente. El resultado es de tipo `SymTridiagonal` y proporciona solucionadores de eigenvalores especializados y eficientes, pero puede ser convertido en una matriz regular con [`convert(Array, _)`](@ref) (o `Array(_)` para abreviar).

Para las matrices de bloques `SymTridiagonal`, los elementos de `dv` son simetrizados. El argumento `ev` se interpreta como la superdiagonal. Los bloques de la subdiagonal son la transposición (materializada) de los bloques correspondientes de la superdiagonal.

# Ejemplos

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> SymTridiagonal(dv, ev)
4×4 SymTridiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 7  2  8  ⋅
 ⋅  8  3  9
 ⋅  ⋅  9  4

julia> A = SymTridiagonal(fill([1 2; 3 4], 3), fill([1 2; 3 4], 2));

julia> A[1,1]
2×2 Symmetric{Int64, Matrix{Int64}}:
 1  2
 2  4

julia> A[1,2]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> A[2,1]
2×2 Matrix{Int64}:
 1  3
 2  4
```
