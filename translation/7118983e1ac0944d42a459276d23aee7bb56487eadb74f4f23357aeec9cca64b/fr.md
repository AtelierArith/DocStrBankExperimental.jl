```
mul!(Y, A, B) -> Y
```

Calcule le produit matrice-matrice ou matrice-vecteur $A B$ et stocke le résultat dans `Y`, écrasant la valeur existante de `Y`. Notez que `Y` ne doit pas être aliasé avec `A` ou `B`.

# Exemples

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; Y = similar(B);

julia> mul!(Y, A, B) === Y
true

julia> Y
2×2 Matrix{Float64}:
 3.0  3.0
 7.0  7.0

julia> Y == A * B
true
```

# Implémentation

Pour les types de matrices et de vecteurs personnalisés, il est recommandé d'implémenter `mul!` à 5 arguments plutôt que d'implémenter directement `mul!` à 3 arguments si possible.
