```
InexactError(nombre::Symbol, T, val)
```

No se puede convertir exactamente `val` al tipo `T` en un método de la función `nombre`.

# Ejemplos

```jldoctest
julia> convert(Float64, 1+2im)
ERROR: InexactError: Float64(1 + 2im)
Stacktrace:
[...]
```
