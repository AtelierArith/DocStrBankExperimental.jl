```
eachrow(A::AbstractVecOrMat) <: AbstractVector
```

Crea un objeto [`RowSlices`](@ref) que es un vector de filas de la matriz o vector `A`. Las secciones de fila se devuelven como vistas de `AbstractVector` de `A`.

Para la inversa, consulta [`stack`](@ref)`(rows; dims=1)`.

Consulta también [`eachcol`](@ref), [`eachslice`](@ref) y [`mapslices`](@ref).

!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.


!!! compat "Julia 1.9"
    Antes de Julia 1.9, esto devolvía un iterador.


# Ejemplos

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> s = eachrow(a)
2-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2]
 [3, 4]

julia> s[1]
2-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
```
