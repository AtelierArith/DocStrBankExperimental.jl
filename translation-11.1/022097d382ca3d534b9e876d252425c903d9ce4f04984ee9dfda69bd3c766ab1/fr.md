```
reim(A::AbstractArray)
```

Renvoie un tuple de deux tableaux contenant respectivement la partie réelle et la partie imaginaire de chaque entrée dans `A`.

Équivalent à `(real.(A), imag.(A))`, sauf que lorsque `eltype(A) <: Real`, `A` est renvoyé sans copie pour représenter la partie réelle, et que lorsque `A` a zéro dimensions, un tableau à 0 dimensions est renvoyé (plutôt qu'un scalaire).

# Exemples

```jldoctest
julia> reim([1, 2im, 3 + 4im])
([1, 0, 3], [0, 2, 4])

julia> reim(fill(2 - im))
(fill(2), fill(-1))
```
