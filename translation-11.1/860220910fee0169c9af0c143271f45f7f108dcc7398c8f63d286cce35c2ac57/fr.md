```
expm1(x)
```

Calcule précisément $e^x-1$. Cela évite la perte de précision impliquée dans l'évaluation directe de exp(x)-1 pour de petites valeurs de x.

# Exemples

```jldoctest
julia> expm1(1e-16)
1.0e-16

julia> exp(1e-16) - 1
0.0
```
