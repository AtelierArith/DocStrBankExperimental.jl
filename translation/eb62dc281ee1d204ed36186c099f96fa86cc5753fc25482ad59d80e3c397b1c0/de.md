```
Diagonal(V::AbstractVector)
```

Konstruiere eine faule Matrix mit `V` als ihrer Diagonale.

Siehe auch [`UniformScaling`](@ref) für die faule Identitätsmatrix `I`, [`diagm`](@ref) um eine dichte Matrix zu erstellen, und [`diag`](@ref) um diagonale Elemente zu extrahieren.

# Beispiele

```jldoctest
julia> d = Diagonal([1, 10, 100])
3×3 Diagonal{Int64, Vector{Int64}}:
 1   ⋅    ⋅
 ⋅  10    ⋅
 ⋅   ⋅  100

julia> diagm([7, 13])
2×2 Matrix{Int64}:
 7   0
 0  13

julia> ans + I
2×2 Matrix{Int64}:
 8   0
 0  14

julia> I(2)
2×2 Diagonal{Bool, Vector{Bool}}:
 1  ⋅
 ⋅  1
```

!!! Hinweis     Eine einspaltige Matrix wird nicht wie ein Vektor behandelt, sondern ruft stattdessen die Methode `Diagonal(A::AbstractMatrix)` auf, die 1-element `diag(A)` extrahiert:

```jldoctest
julia> A = transpose([7.0 13.0])
2×1 transpose(::Matrix{Float64}) mit eltype Float64:
  7.0
 13.0

julia> Diagonal(A)
1×1 Diagonal{Float64, Vector{Float64}}:
 7.0
```
