```
sizeof(str::AbstractString)
```

Tamaño, en bytes, de la cadena `str`. Igual al número de unidades de código en `str` multiplicado por el tamaño, en bytes, de una unidad de código en `str`.

# Ejemplos

```jldoctest
julia> sizeof("")
0

julia> sizeof("∀")
3
```
