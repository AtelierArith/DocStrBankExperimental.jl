```
extrema(itr; [init]) -> (mn, mx)
```

Calcula tanto el elemento mínimo `mn` como el máximo `mx` en una sola pasada y los devuelve como una tupla de 2 elementos.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser una tupla de 2 elementos cuyos primeros y segundos elementos son elementos neutros para `min` y `max` respectivamente (es decir, que son mayores/menores o iguales a cualquier otro elemento). Como consecuencia, cuando `itr` está vacío, la tupla devuelta `(mn, mx)` satisfará `mn ≥ mx`. Cuando `init` es especificado, puede ser utilizado incluso para `itr` no vacío.

!!! compat "Julia 1.8"
    El argumento clave `init` requiere Julia 1.8 o posterior.


# Ejemplos

```jldoctest
julia> extrema(2:10)
(2, 10)

julia> extrema([9,pi,4.5])
(3.141592653589793, 9.0)

julia> extrema([]; init = (Inf, -Inf))
(Inf, -Inf)
```
