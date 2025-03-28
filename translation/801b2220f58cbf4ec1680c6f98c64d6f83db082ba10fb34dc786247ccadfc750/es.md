```
rationalize([T<:Integer=Int,] x; tol::Real=eps(x))
```

Aproximar el número de punto flotante `x` como un número [`Rational`](@ref) con componentes del tipo de entero dado. El resultado diferirá de `x` por no más de `tol`.

# Ejemplos

```jldoctest
julia> rationalize(5.6)
28//5

julia> a = rationalize(BigInt, 10.3)
103//10

julia> typeof(numerator(a))
BigInt
```
