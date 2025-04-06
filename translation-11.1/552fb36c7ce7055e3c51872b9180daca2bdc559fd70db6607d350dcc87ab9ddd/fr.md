```
gcdx(a, b)
```

Calcule le plus grand commun diviseur (positif) de `a` et `b` ainsi que leurs coefficients de Bézout, c'est-à-dire les coefficients entiers `u` et `v` qui satisfont $ua+vb = d = gcd(a, b)$. `gcdx(a, b)` retourne $(d, u, v)$.

Les arguments peuvent être des nombres entiers et rationnels.

!!! compat "Julia 1.4"
    Les arguments rationnels nécessitent Julia 1.4 ou une version ultérieure.


# Exemples

```jldoctest
julia> gcdx(12, 42)
(6, -3, 1)

julia> gcdx(240, 46)
(2, -9, 47)
```

!!! note
    Les coefficients de Bézout ne sont *pas* définis de manière unique. `gcdx` retourne les coefficients de Bézout minimaux qui sont calculés par l'algorithme d'Euclide étendu. (Réf : D. Knuth, TAoCP, 2/e, p. 325, Algorithme X.) Pour les entiers signés, ces coefficients `u` et `v` sont minimaux au sens où $|u| < |b/d|$ et $|v| < |a/d|$. De plus, les signes de `u` et `v` sont choisis de sorte que `d` soit positif. Pour les entiers non signés, les coefficients `u` et `v` peuvent être proches de leur `typemax`, et l'identité ne tient alors que via l'arithmétique modulo des entiers non signés.

