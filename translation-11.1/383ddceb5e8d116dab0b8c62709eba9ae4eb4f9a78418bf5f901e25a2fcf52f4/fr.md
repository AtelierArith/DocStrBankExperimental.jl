```
issuccess(F::LU; allowsingular = false)
```

Testez si la factorisation LU d'une matrice a réussi. Par défaut, une factorisation qui produit un facteur U valide mais de rang déficient est considérée comme un échec. Cela peut être modifié en passant `allowsingular = true`.

!!! compat "Julia 1.11"
    L'argument clé `allowsingular` a été ajouté dans Julia 1.11.


# Exemples

```jldoctest
julia> F = lu([1 2; 1 2], check = false);

julia> issuccess(F)
false

julia> issuccess(F, allowsingular = true)
true
```
