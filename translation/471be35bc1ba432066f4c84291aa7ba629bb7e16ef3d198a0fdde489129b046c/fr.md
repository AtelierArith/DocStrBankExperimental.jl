```
InexactError(name::Symbol, T, val)
```

Impossible de convertir exactement `val` en type `T` dans une méthode de la fonction `name`.

# Exemples

```jldoctest
julia> convert(Float64, 1+2im)
ERROR: InexactError: Float64(1 + 2im)
Stacktrace:
[...]
```
