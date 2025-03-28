```
@uint128_str str
```

Analiza `str` como un [`UInt128`](@ref). Lanza un `ArgumentError` si la cadena no es un entero válido.

# Ejemplos

```
julia> uint128"123456789123"
0x00000000000000000000001cbe991a83

julia> uint128"-123456789123"
ERROR: LoadError: ArgumentError: invalid base 10 digit '-' in "-123456789123"
[...]
```
