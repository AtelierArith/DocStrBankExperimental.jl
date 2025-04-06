```
atan(y)
atan(y, x)
```

Calcule l'arc tangente de `y` ou de `y/x`, respectivement.

Pour un argument réel, c'est l'angle en radians entre l'axe *x* positif et le point (1, *y*), retournant une valeur dans l'intervalle $[-\pi/2, \pi/2]$.

Pour deux arguments, c'est l'angle en radians entre l'axe *x* positif et le point (*x*, *y*), retournant une valeur dans l'intervalle $[-\pi, \pi]$. Cela correspond à une fonction [`atan2`](https://en.wikipedia.org/wiki/Atan2) standard. Notez qu'en convention `atan(0.0,x)` est défini comme $\pi$ et `atan(-0.0,x)` est défini comme $-\pi$ lorsque `x < 0`.

Voir aussi [`atand`](@ref) pour les degrés.

# Exemples

```jldoctest
julia> rad2deg(atan(-1/√3))
-30.000000000000004

julia> rad2deg(atan(-1, √3))
-30.000000000000004

julia> rad2deg(atan(1, -√3))
150.0
```
