```
maximum(itr; [init])
```

Devuelve el elemento más grande en una colección.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser un elemento neutro para `max` (es decir, que sea menor o igual que cualquier otro elemento) ya que no está especificado si `init` se utiliza para colecciones no vacías.

!!! compat "Julia 1.6"
    El argumento de palabra clave `init` requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> maximum(-20.5:10)
9.5

julia> maximum([1,2,3])
3

julia> maximum(())
ERROR: ArgumentError: reducir sobre una colección vacía no está permitido; considera proporcionar `init` al reductor
Stacktrace:
[...]

julia> maximum((); init=-Inf)
-Inf
```
