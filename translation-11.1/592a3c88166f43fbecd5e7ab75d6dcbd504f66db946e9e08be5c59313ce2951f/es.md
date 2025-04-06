```
@big_str str
```

Analiza una cadena en un [`BigInt`](@ref) o [`BigFloat`](@ref), y lanza un `ArgumentError` si la cadena no es un número válido. Para enteros, se permite `_` en la cadena como separador.

# Ejemplos

```jldoctest
julia> big"123_456"
123456

julia> big"7891.5"
7891.5

julia> big"_"
ERROR: ArgumentError: formato de número inválido _ para BigInt o BigFloat
[...]
```

!!! advertencia
    Usar `@big_str` para construir valores de [`BigFloat`](@ref) puede no resultar en el comportamiento que podría esperarse ingenuamente: como una macro, `@big_str` obedece la precisión global ([`setprecision`](@ref)) y la configuración del modo de redondeo ([`setrounding`](@ref)) tal como están en el *tiempo de carga*. Así, una función como `() -> precision(big"0.3")` devuelve una constante cuyo valor depende del valor de la precisión en el momento en que se define la función, **no** en la precisión en el momento en que se llama a la función.

