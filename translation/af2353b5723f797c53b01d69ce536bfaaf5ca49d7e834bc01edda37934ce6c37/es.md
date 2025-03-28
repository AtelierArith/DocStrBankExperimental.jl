```
maximum(f, itr; [init])
```

Devuelve el resultado más grande de llamar a la función `f` en cada elemento de `itr`.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser un elemento neutro para `max` (es decir, que sea menor o igual que cualquier otro elemento) ya que no está especificado si `init` se utiliza para colecciones no vacías.

!!! compat "Julia 1.6"
    El argumento clave `init` requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> maximum(length, ["Julion", "Julia", "Jule"])
6

julia> maximum(length, []; init=-1)
-1

julia> maximum(sin, Real[]; init=-1.0)  # bien, ya que la salida de sin es >= -1
-1.0
```
