```
unique!(f, A::AbstractVector)
```

Selecciona un valor de `A` para cada valor único producido por `f` aplicado a los elementos de `A`, y luego devuelve el `A` modificado.

!!! compat "Julia 1.1"
    Este método está disponible desde Julia 1.1.


# Ejemplos

```jldoctest
julia> unique!(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4

julia> unique!(n -> n%3, [5, 1, 8, 9, 3, 4, 10, 7, 2, 6])
3-element Vector{Int64}:
 5
 1
 9

julia> unique!(iseven, [2, 3, 5, 7, 9])
2-element Vector{Int64}:
 2
 3
```
