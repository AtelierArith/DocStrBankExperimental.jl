```
minimum(itr; [init])
```

Devuelve el elemento más pequeño en una colección.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser un elemento neutro para `min` (es decir, que sea mayor o igual que cualquier otro elemento) ya que no está especificado si `init` se utiliza para colecciones no vacías.

!!! compat "Julia 1.6"
    El argumento clave `init` requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> minimum(-20.5:10)
-20.5

julia> minimum([1,2,3])
1

julia> minimum([])
ERROR: ArgumentError: reducir sobre una colección vacía no está permitido; considera proporcionar `init` al reductor
Stacktrace:
[...]

julia> minimum([]; init=Inf)
Inf
```
