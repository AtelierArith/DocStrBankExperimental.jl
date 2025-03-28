```
LinearAlgebra.Givens(i1,i2,c,s) -> G
```

Un opérateur linéaire de rotation de Givens. Les champs `c` et `s` représentent le cosinus et le sinus de l'angle de rotation, respectivement. Le type `Givens` prend en charge la multiplication à gauche `G*A` et la multiplication par la transposée conjuguée à droite `A*G'`. Le type n'a pas de `size` et peut donc être multiplié avec des matrices de taille arbitraire tant que `i2<=size(A,2)` pour `G*A` ou `i2<=size(A,1)` pour `A*G'`.

Voir aussi [`givens`](@ref).
