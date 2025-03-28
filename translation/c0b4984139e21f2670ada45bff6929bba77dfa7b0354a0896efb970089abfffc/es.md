```
muladd(A, y, z)
```

Multiplicación-suma combinada, `A*y .+ z`, para multiplicación de matriz-matriz o matriz-vector. El resultado siempre tiene el mismo tamaño que `A*y`, pero `z` puede ser más pequeño o un escalar.

!!! compat "Julia 1.6"
    Estos métodos requieren Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> A=[1.0 2.0; 3.0 4.0]; B=[1.0 1.0; 1.0 1.0]; z=[0, 100];

julia> muladd(A, B, z)
2×2 Matrix{Float64}:
   3.0    3.0
 107.0  107.0
```
