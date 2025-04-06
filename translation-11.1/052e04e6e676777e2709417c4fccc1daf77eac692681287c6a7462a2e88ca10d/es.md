```
@int128_str str
```

Analiza `str` como un [`Int128`](@ref). Lanza un `ArgumentError` si la cadena no es un entero válido.

# Ejemplos

```jldoctest
julia> int128"123456789123"
123456789123

julia> int128"123456789123.4"
ERROR: LoadError: ArgumentError: invalid base 10 digit '.' in "123456789123.4"
[...]
```
