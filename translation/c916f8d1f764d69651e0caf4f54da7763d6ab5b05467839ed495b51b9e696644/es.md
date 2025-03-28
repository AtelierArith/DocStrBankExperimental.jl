```
extrema(f, itr; [init]) -> (mn, mx)
```

Calcula tanto el mínimo `mn` como el máximo `mx` de `f` aplicado a cada elemento en `itr` y los devuelve como una tupla de 2 elementos. Solo se realiza un pase sobre `itr`.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser una tupla de 2 elementos cuyos primeros y segundos elementos son elementos neutros para `min` y `max` respectivamente (es decir, que son mayores/menores o iguales a cualquier otro elemento). Se utiliza para colecciones no vacías. Nota: implica que, para `itr` vacío, el valor devuelto `(mn, mx)` satisface `mn ≥ mx` aunque para `itr` no vacío satisface `mn ≤ mx`. Este es un resultado "paradójico" pero aún así esperado.

!!! compat "Julia 1.2"
    Este método requiere Julia 1.2 o posterior.


!!! compat "Julia 1.8"
    El argumento clave `init` requiere Julia 1.8 o posterior.


# Ejemplos

```jldoctest
julia> extrema(sin, 0:π)
(0.0, 0.9092974268256817)

julia> extrema(sin, Real[]; init = (1.0, -1.0))  # bien, ya que -1 ≤ sin(::Real) ≤ 1
(1.0, -1.0)
```
