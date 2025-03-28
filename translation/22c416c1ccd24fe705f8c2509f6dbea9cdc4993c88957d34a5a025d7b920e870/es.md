```
mod1(x, y)
```

Módulo después de la división por piso, devolviendo un valor `r` tal que `mod(r, y) == mod(x, y)` en el rango $(0, y]$ para `y` positivo y en el rango $[y,0)$ para `y` negativo.

Con argumentos enteros y `y` positivo, esto es igual a `mod(x, 1:y)`, y por lo tanto es natural para la indexación basada en 1. En comparación, `mod(x, y) == mod(x, 0:y-1)` es natural para cálculos con desplazamientos o saltos.

Véase también [`mod`](@ref), [`fld1`](@ref), [`fldmod1`](@ref).

# Ejemplos

```jldoctest
julia> mod1(4, 2)
2

julia> mod1.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  3  1  2  3  1  2  3  1  2

julia> mod1.([-0.1, 0, 0.1, 1, 2, 2.9, 3, 3.1]', 3)
1×8 Matrix{Float64}:
 2.9  3.0  0.1  1.0  2.0  2.9  3.0  0.1
```
