```
DivideError()
```

Se intentó una división entera con un valor de denominador de 0.

# Ejemplos

```jldoctest
julia> 2/0
Inf

julia> div(2, 0)
ERROR: DivideError: error de división entera
Stacktrace:
[...]
```
