```
Symmetric(A::AbstractMatrix, uplo::Symbol=:U)
```

Construit une vue `Symmetric` du triangle supérieur (si `uplo = :U`) ou inférieur (si `uplo = :L`) de la matrice `A`.

Les vues `Symmetric` sont principalement utiles pour les matrices réelles symétriques, pour lesquelles des algorithmes spécialisés (par exemple pour les problèmes propres) sont activés pour les types `Symmetric`. Plus généralement, voir aussi [`Hermitian(A)`](@ref) pour les matrices hermitiennes `A == A'`, qui est effectivement équivalent à `Symmetric` pour les matrices réelles mais est également utile pour les matrices complexes. (Alors que les matrices `Symmetric` complexes sont prises en charge mais ont peu, voire aucun, algorithme spécialisé.)

Pour calculer la partie symétrique d'une matrice réelle, ou plus généralement la partie hermitienne `(A + A') / 2` d'une matrice réelle ou complexe `A`, utilisez [`hermitianpart`](@ref).

# Exemples

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> Supper = Symmetric(A)
3×3 Symmetric{Int64, Matrix{Int64}}:
 1  2  3
 2  5  6
 3  6  9

julia> Slower = Symmetric(A, :L)
3×3 Symmetric{Int64, Matrix{Int64}}:
 1  4  7
 4  5  8
 7  8  9

julia> hermitianpart(A)
3×3 Hermitian{Float64, Matrix{Float64}}:
 1.0  3.0  5.0
 3.0  5.0  7.0
 5.0  7.0  9.0
```

Notez que `Supper` ne sera pas égal à `Slower` à moins que `A` ne soit elle-même symétrique (par exemple si `A == transpose(A)`).
