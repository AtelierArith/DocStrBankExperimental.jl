```
opnorm(A::Adjoint{<:Any,<:AbstractVector}, q::Real=2)
opnorm(A::Transpose{<:Any,<:AbstractVector}, q::Real=2)
```

Pour les vecteurs enveloppés dans Adjoint/Transpose, renvoie la norme opérateur $q$-norm de `A`, qui est équivalente à la `p`-norm avec la valeur `p = q/(q-1)`. Elles coïncident à `p = q = 2`. Utilisez [`norm`](@ref) pour calculer la norme `p` de `A` en tant que vecteur.

La différence de norme entre un espace vectoriel et son dual apparaît pour préserver la relation entre la dualité et le produit scalaire, et le résultat est cohérent avec la norme opérateur `p` d'une matrice `1 × n`.

# Exemples

```jldoctest
julia> v = [1; im];

julia> vc = v';

julia> opnorm(vc, 1)
1.0

julia> norm(vc, 1)
2.0

julia> norm(v, 1)
2.0

julia> opnorm(vc, 2)
1.4142135623730951

julia> norm(vc, 2)
1.4142135623730951

julia> norm(v, 2)
1.4142135623730951

julia> opnorm(vc, Inf)
2.0

julia> norm(vc, Inf)
1.0

julia> norm(v, Inf)
1.0
```
