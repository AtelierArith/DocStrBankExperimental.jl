```
imag(A::AbstractArray)
```

Renvoie un tableau contenant la partie imaginaire de chaque entrée dans le tableau `A`.

Équivalent à `imag.(A)`, sauf que lorsque `A` a zéro dimension, un tableau à 0 dimension est renvoyé (plutôt qu'un scalaire).

# Exemples

```jldoctest
julia> imag([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 0
 2
 4

julia> imag(fill(2 - im))
0-dimensional Array{Int64, 0}:
-1
```
