```
diff(A::AbstractVector)
diff(A::AbstractArray; dims::Integer)
```

Operador de diferencia finita en un vector o un arreglo multidimensional `A`. En el último caso, la dimensión sobre la que operar debe especificarse con el argumento de palabra clave `dims`.

!!! compat "Julia 1.1"
    `diff` para arreglos con dimensión mayor que 2 requiere al menos Julia 1.1.


# Ejemplos

```jldoctest
julia> a = [2 4; 6 16]
2×2 Matrix{Int64}:
 2   4
 6  16

julia> diff(a, dims=2)
2×1 Matrix{Int64}:
  2
 10

julia> diff(vec(a))
3-element Vector{Int64}:
  4
 -2
 12
```
