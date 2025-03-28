```
lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC; check=true, reuse_symbolic=true, q=nothing) -> F::UmfpackLU
```

Calcule la factorisation LU d'une matrice creuse `A`, réutilisant la factorisation symbolique d'une factorisation LU déjà existante stockée dans `F`. À moins que `reuse_symbolic` ne soit défini sur false, la matrice creuse `A` doit avoir un motif de non-zéros identique à la matrice utilisée pour créer la factorisation LU `F`, sinon une erreur est levée. Si la taille de `A` et `F` diffère, tous les vecteurs seront redimensionnés en conséquence.

Lorsque `check = true`, une erreur est levée si la décomposition échoue. Lorsque `check = false`, la responsabilité de vérifier la validité de la décomposition (via [`issuccess`](@ref)) incombe à l'utilisateur.

La permutation `q` peut être soit un vecteur de permutation, soit `nothing`. Si aucun vecteur de permutation n'est fourni ou si `q` est `nothing`, le défaut d'UMFPACK est utilisé. Si la permutation n'est pas basée sur zéro, une copie basée sur zéro est faite.

Voir aussi [`lu`](@ref)

!!! note
    `lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC)` utilise la bibliothèque UMFPACK qui fait partie de SuiteSparse. Comme cette bibliothèque ne prend en charge que les matrices creuses avec des éléments [`Float64`](@ref) ou `ComplexF64`, `lu!` convertira automatiquement les types en ceux définis par la factorisation LU ou `SparseMatrixCSC{ComplexF64}` selon le cas.


!!! compat "Julia 1.5"
    `lu!` pour `UmfpackLU` nécessite au moins Julia 1.5.


# Exemples

```jldoctest
julia> A = sparse(Float64[1.0 2.0; 0.0 3.0]);

julia> F = lu(A);

julia> B = sparse(Float64[1.0 1.0; 0.0 1.0]);

julia> lu!(F, B);

julia> F \ ones(2)
2-element Vector{Float64}:
 0.0
 1.0
```
