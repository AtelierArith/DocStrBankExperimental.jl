```
eachcol(A::AbstractVecOrMat) <: AbstractVector
```

Erstellt ein [`ColumnSlices`](@ref) Objekt, das ein Vektor von Spalten der Matrix oder des Vektors `A` ist. Spaltenausschnitte werden als `AbstractVector` Ansichten von `A` zurückgegeben.

Für das Gegenteil siehe [`stack`](@ref)`(cols)` oder `reduce(`[`hcat`](@ref)`, cols)`.

Siehe auch [`eachrow`](@ref), [`eachslice`](@ref) und [`mapslices`](@ref).

!!! compat "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1.


!!! compat "Julia 1.9"
    Vor Julia 1.9 gab dies einen Iterator zurück.


# Beispiele

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
