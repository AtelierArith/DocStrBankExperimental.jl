```
UniformScaling{T<:Number}
```

Operador de escalado uniforme de tamaño genérico definido como un escalar multiplicado por el operador identidad, `λ*I`. Aunque sin un `size` explícito, actúa de manera similar a una matriz en muchos casos e incluye soporte para algunos índices. Ver también [`I`](@ref).

!!! compat "Julia 1.6"
    La indexación utilizando rangos está disponible a partir de Julia 1.6.


# Ejemplos

```jldoctest
julia> J = UniformScaling(2.)
UniformScaling{Float64}
2.0*I

julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> J*A
2×2 Matrix{Float64}:
 2.0  4.0
 6.0  8.0

julia> J[1:2, 1:2]
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
