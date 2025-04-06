```
eachcol(A::AbstractVecOrMat) <: AbstractVector
```

Crea un objeto [`ColumnSlices`](@ref) que es un vector de columnas de la matriz o vector `A`. Los cortes de columna se devuelven como vistas de `AbstractVector` de `A`.

Para la inversa, consulta [`stack`](@ref)`(cols)` o `reduce(`[`hcat`](@ref)`, cols)`.

Consulta también [`eachrow`](@ref), [`eachslice`](@ref) y [`mapslices`](@ref).

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

julia> s = eachcol(a)
2-element ColumnSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Base.Slice{Base.OneTo{Int64}}, Int64}, true}}:
 [1, 3]
 [2, 4]

julia> s[1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3
```
