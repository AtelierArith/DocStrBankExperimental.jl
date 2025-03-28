```
unsafe_trunc(T, x)
```

Devuelve el valor integral más cercano del tipo `T` cuyo valor absoluto es menor o igual al valor absoluto de `x`. Si el valor no es representable por `T`, se devolverá un valor arbitrario. Ver también [`trunc`](@ref).

# Ejemplos

```jldoctest
julia> unsafe_trunc(Int, -2.2)
-2

julia> unsafe_trunc(Int, NaN)
-9223372036854775808
```
