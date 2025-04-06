```
inv(x)
```

Devuelve el inverso multiplicativo de `x`, de tal manera que `x*inv(x)` o `inv(x)*x` produce [`one(x)`](@ref) (la identidad multiplicativa) hasta errores de redondeo.

Si `x` es un número, esto es esencialmente lo mismo que `one(x)/x`, pero para algunos tipos `inv(x)` puede ser ligeramente más eficiente.

# Ejemplos

```jldoctest
julia> inv(2)
0.5

julia> inv(1 + 2im)
0.2 - 0.4im

julia> inv(1 + 2im) * (1 + 2im)
1.0 + 0.0im

julia> inv(2//3)
3//2
```

!!! compat "Julia 1.2"
    `inv(::Missing)` requiere al menos Julia 1.2.

