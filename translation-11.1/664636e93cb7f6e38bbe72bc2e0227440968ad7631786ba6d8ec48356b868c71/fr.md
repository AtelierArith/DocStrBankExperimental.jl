```
transpose(A)
```

Transposition paresseuse. La mutation de l'objet retourné doit muter `A` de manière appropriée. Souvent, mais pas toujours, cela donne `Transpose(A)`, où `Transpose` est un wrapper de transposition paresseuse. Notez que cette opération est récursive.

Cette opération est destinée à un usage en algèbre linéaire - pour la manipulation générale des données, voir [`permutedims`](@ref Base.permutedims), qui est non récursive.

# Exemples

```jldoctest
julia> A = [3 2; 0 0]
2×2 Matrix{Int64}:
 3  2
 0  0

julia> B = transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 3  0
 2  0

julia> B isa Transpose
true

julia> transpose(B) === A # la transposition d'une transposition déplie le parent
true

julia> Transpose(B) # cependant, le constructeur enveloppe toujours son argument
2×2 transpose(transpose(::Matrix{Int64})) with eltype Int64:
 3  2
 0  0

julia> B[1,2] = 4; # modifier B modifiera automatiquement A

julia> A
2×2 Matrix{Int64}:
 3  2
 4  0
```

Pour les matrices complexes, l'opération `adjoint` est équivalente à une transposition conjuguée.

```jldoctest
julia> A = reshape([Complex(x, x) for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> adjoint(A) == conj(transpose(A))
true
```

La `transpose` d'un `AbstractVector` est un vecteur ligne :

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> transpose(v) # retourne un vecteur ligne
1×3 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3

julia> transpose(v) * v # calcule le produit scalaire
14
```

Pour une matrice de matrices, les blocs individuels sont opérés de manière récursive :

```jldoctest
julia> C = [1 3; 2 4]
2×2 Matrix{Int64}:
 1  3
 2  4

julia> D = reshape([C, 2C, 3C, 4C], 2, 2) # construire une matrice bloc
2×2 Matrix{Matrix{Int64}}:
 [1 3; 2 4]  [3 9; 6 12]
 [2 6; 4 8]  [4 12; 8 16]

julia> transpose(D) # les blocs sont transposés de manière récursive
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 2; 3 4]   [2 4; 6 8]
 [3 6; 9 12]  [4 8; 12 16]
```
