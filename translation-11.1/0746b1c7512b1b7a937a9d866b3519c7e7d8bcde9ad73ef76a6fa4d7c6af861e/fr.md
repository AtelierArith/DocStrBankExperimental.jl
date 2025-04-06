```
A'
adjoint(A)
```

Adjoint paresseux (transposition conjuguée). Notez que `adjoint` est appliqué de manière récursive aux éléments.

Pour les types numériques, `adjoint` renvoie le conjugué complexe, et donc il est équivalent à la fonction identité pour les nombres réels.

Cette opération est destinée à une utilisation en algèbre linéaire - pour la manipulation générale des données, voir [`permutedims`](@ref Base.permutedims).

# Exemples

```jldoctest
julia> A = [3+2im 9+2im; 0  0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> B = A' # équivalent à adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im

julia> B isa Adjoint
true

julia> adjoint(B) === A # l'adjoint d'un adjoint déplie le parent
true

julia> Adjoint(B) # cependant, le constructeur enveloppe toujours son argument
2×2 adjoint(adjoint(::Matrix{Complex{Int64}})) with eltype Complex{Int64}:
 3+2im  9+2im
 0+0im  0+0im

julia> B[1,2] = 4 + 5im; # modifier B modifiera automatiquement A

julia> A
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 4-5im  0+0im
```

Pour les matrices réelles, l'opération `adjoint` est équivalente à une `transpose`.

```jldoctest
julia> A = reshape([x for x in 1:4], 2, 2)
2×2 Matrix{Int64}:
 1  3
 2  4

julia> A'
2×2 adjoint(::Matrix{Int64}) with eltype Int64:
 1  2
 3  4

julia> adjoint(A) == transpose(A)
true
```

L'adjoint d'un `AbstractVector` est un vecteur ligne :

```jldoctest
julia> x = [3, 4im]
2-element Vector{Complex{Int64}}:
 3 + 0im
 0 + 4im

julia> x'
1×2 adjoint(::Vector{Complex{Int64}}) with eltype Complex{Int64}:
 3+0im  0-4im

julia> x'x # calculer le produit scalaire, équivalent à x' * x
25 + 0im
```

Pour une matrice de matrices, les blocs individuels sont opérés de manière récursive :

```jldoctest
julia> A = reshape([x + im*x for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> C = reshape([A, 2A, 3A, 4A], 2, 2)
2×2 Matrix{Matrix{Complex{Int64}}}:
 [1+1im 3+3im; 2+2im 4+4im]  [3+3im 9+9im; 6+6im 12+12im]
 [2+2im 6+6im; 4+4im 8+8im]  [4+4im 12+12im; 8+8im 16+16im]

julia> C'
2×2 adjoint(::Matrix{Matrix{Complex{Int64}}}) with eltype Adjoint{Complex{Int64}, Matrix{Complex{Int64}}}:
 [1-1im 2-2im; 3-3im 4-4im]    [2-2im 4-4im; 6-6im 8-8im]
 [3-3im 6-6im; 9-9im 12-12im]  [4-4im 8-8im; 12-12im 16-16im]
```
