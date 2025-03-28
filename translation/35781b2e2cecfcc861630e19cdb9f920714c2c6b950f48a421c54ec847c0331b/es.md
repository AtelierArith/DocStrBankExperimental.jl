```
only(x)
```

Devuelve el único y único elemento de la colección `x`, o lanza un [`ArgumentError`](@ref) si la colección tiene cero o múltiples elementos.

Véase también [`first`](@ref), [`last`](@ref).

!!! compat "Julia 1.4"
    Este método requiere al menos Julia 1.4.


# Ejemplos

```jldoctest
julia> only(["a"])
"a"

julia> only("a")
'a': ASCII/Unicode U+0061 (categoría Ll: Letra, minúscula)

julia> only(())
ERROR: ArgumentError: El tuple contiene 0 elementos, debe contener exactamente 1 elemento
Stacktrace:
[...]

julia> only(('a', 'b'))
ERROR: ArgumentError: El tuple contiene 2 elementos, debe contener exactamente 1 elemento
Stacktrace:
[...]
```
