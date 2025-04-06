```
randsubseq([rng=default_rng(),] A, p) -> Vector
```

Retourne un vecteur consistant en une sous-séquence aléatoire du tableau donné `A`, où chaque élément de `A` est inclus (dans l'ordre) avec une probabilité indépendante `p`. (La complexité est linéaire en `p*length(A)`, donc cette fonction est efficace même si `p` est petit et `A` est grand.) Techniquement, ce processus est connu sous le nom de "sampling de Bernoulli" de `A`.

# Exemples

```jldoctest
julia> randsubseq(Xoshiro(123), 1:8, 0.3)
2-element Vector{Int64}:
 4
 7
```
