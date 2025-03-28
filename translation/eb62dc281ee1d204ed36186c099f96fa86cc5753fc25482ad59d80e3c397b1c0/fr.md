```
Diagonal(V::AbstractVector)
```

Construit une matrice paresseuse avec `V` comme sa diagonale.

Voir aussi [`UniformScaling`](@ref) pour la matrice identité paresseuse `I`, [`diagm`](@ref) pour créer une matrice dense, et [`diag`](@ref) pour extraire les éléments diagonaux.

# Exemples

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

!!! note
    Une matrice à une colonne n'est pas traitée comme un vecteur, mais appelle plutôt la méthode `Diagonal(A::AbstractMatrix)` qui extrait `1` élément `diag(A)`:


```jldoctest
julia> A = transpose([7.0 13.0])
2×1 transpose(::Matrix{Float64}) avec eltype Float64:
  7.0
 13.0

julia> Diagonal(A)
1×1 Diagonal{Float64, Vector{Float64}}:
 7.0
```
