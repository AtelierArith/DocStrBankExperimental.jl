```
eachrow(A::AbstractVecOrMat) <: AbstractVector
```

Erstellt ein [`RowSlices`](@ref) Objekt, das ein Vektor von Zeilen der Matrix oder des Vektors `A` ist. Zeilen-Slices werden als `AbstractVector` Ansichten von `A` zurückgegeben.

Für das Gegenteil siehe [`stack`](@ref)`(rows; dims=1)`.

Siehe auch [`eachcol`](@ref), [`eachslice`](@ref) und [`mapslices`](@ref).

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

julia> s = eachrow(a)
2-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2]
 [3, 4]

julia> s[1]
2-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
```
