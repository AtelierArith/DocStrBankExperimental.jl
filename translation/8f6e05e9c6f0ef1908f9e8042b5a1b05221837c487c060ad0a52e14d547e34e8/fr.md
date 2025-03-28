```
conj(A::AbstractArray)
```

Renvoie un tableau contenant le conjugué complexe de chaque entrée dans le tableau `A`.

Équivalent à `conj.(A)`, sauf que lorsque `eltype(A) <: Real`, `A` est renvoyé sans copie, et que lorsque `A` a zéro dimensions, un tableau à 0 dimensions est renvoyé (plutôt qu'un scalaire).

# Exemples

```jldoctest
julia> conj([1, 2im, 3 + 4im])
3-element Vector{Complex{Int64}}:
 1 + 0im
 0 - 2im
 3 - 4im

julia> conj(fill(2 - im))
0-dimensional Array{Complex{Int64}, 0}:
2 + 1im
```
