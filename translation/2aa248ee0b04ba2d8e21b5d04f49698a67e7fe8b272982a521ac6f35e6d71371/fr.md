```
real(A::AbstractArray)
```

Renvoie un tableau contenant la partie réelle de chaque entrée dans le tableau `A`.

Équivalent à `real.(A)`, sauf que lorsque `eltype(A) <: Real`, `A` est renvoyé sans copie, et que lorsque `A` a zéro dimensions, un tableau à 0 dimensions est renvoyé (plutôt qu'un scalaire).

# Exemples

```jldoctest
julia> real([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 1
 0
 3

julia> real(fill(2 - im))
0-dimensional Array{Int64, 0}:
2
```
