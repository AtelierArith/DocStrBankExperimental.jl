```
fld(x, y)
```

El entero más grande menor o igual a `x / y`. Equivalente a `div(x, y, RoundDown)`.

Véase también [`div`](@ref), [`cld`](@ref), [`fld1`](@ref).

# Ejemplos

```jldoctest
julia> fld(7.3, 5.5)
1.0

julia> fld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) con el tipo de elemento Int64:
 -2  -2  -1  -1  -1  0  0  0  1  1  1
```

Debido a que `fld(x, y)` implementa un redondeo hacia abajo estrictamente correcto basado en el valor verdadero de los números de punto flotante, pueden surgir situaciones poco intuitivas. Por ejemplo:

```jldoctest
julia> fld(6.0, 0.1)
59.0
julia> 6.0 / 0.1
60.0
julia> 6.0 / big(0.1)
59.99999999999999666933092612453056361837965690217069245739573412231113406246995
```

Lo que está sucediendo aquí es que el valor verdadero del número de punto flotante escrito como `0.1` es ligeramente mayor que el valor numérico 1/10, mientras que `6.0` representa el número 6 con precisión. Por lo tanto, el valor verdadero de `6.0 / 0.1` es ligeramente menor que 60. Al hacer la división, esto se redondea a precisamente `60.0`, pero `fld(6.0, 0.1)` siempre toma el piso del valor verdadero, por lo que el resultado es `59.0`.
