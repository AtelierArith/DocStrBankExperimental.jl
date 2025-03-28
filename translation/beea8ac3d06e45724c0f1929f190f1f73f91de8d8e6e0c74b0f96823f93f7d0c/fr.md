```
fma(x, y, z)
```

Calcule `x*y+z` sans arrondir le résultat intermédiaire `x*y`. Sur certains systèmes, cela coûte significativement plus cher que `x*y+z`. `fma` est utilisé pour améliorer la précision dans certains algorithmes. Voir [`muladd`](@ref).
