```
ldiv!(Y, A, B) -> Y
```

Calcule `A \ B` sur place et stocke le résultat dans `Y`, en retournant le résultat.

L'argument `A` ne doit *pas* être une matrice. Au lieu de matrices, il doit s'agir d'un objet de factorisation (par exemple, produit par [`factorize`](@ref) ou [`cholesky`](@ref)). La raison en est que la factorisation elle-même est à la fois coûteuse et nécessite généralement d'allouer de la mémoire (bien qu'elle puisse également être effectuée sur place via, par exemple, [`lu!`](@ref)), et les situations critiques en termes de performance nécessitant `ldiv!` exigent généralement un contrôle fin sur la factorisation de `A`.

!!! note
    Certains types de matrices structurées, tels que `Diagonal` et `UpperTriangular`, sont autorisés, car ils sont déjà sous une forme factorisée.


# Exemples

```jldoctest
julia> A = [1 2.2 4; 3.1 0.2 3; 4 1 2];

julia> X = [1; 2.5; 3];

julia> Y = zero(X);

julia> ldiv!(Y, qr(A), X);

julia> Y ≈ A\X
true
```
