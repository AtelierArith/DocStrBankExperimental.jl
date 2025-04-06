```
InexactError(name::Symbol, T, val)
```

Kann `val` nicht genau in den Typ `T` in einer Methode der Funktion `name` umwandeln.

# Beispiele

```jldoctest
julia> convert(Float64, 1+2im)
ERROR: InexactError: Float64(1 + 2im)
Stacktrace:
[...]
```
