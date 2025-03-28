```
setdiff!(s, itrs...)
```

Elimina del conjunto `s` (in situ) cada elemento de cada iterable de `itrs`. Mantiene el orden con arreglos.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


# Ejemplos

```jldoctest
julia> a = Set([1, 3, 4, 5]);

julia> setdiff!(a, 1:2:6);

julia> a
Set{Int64} con 1 elemento:
  4
```
