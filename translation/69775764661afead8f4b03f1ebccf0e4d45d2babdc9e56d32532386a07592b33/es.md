```
minimum(f, itr; [init])
```

Devuelve el resultado más pequeño de llamar a la función `f` en cada elemento de `itr`.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser un elemento neutro para `min` (es decir, que sea mayor o igual que cualquier otro elemento) ya que no está especificado si `init` se utiliza para colecciones no vacías.

!!! compat "Julia 1.6"
    El argumento clave `init` requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> minimum(length, ["Julion", "Julia", "Jule"])
4

julia> minimum(length, []; init=typemax(Int64))
9223372036854775807

julia> minimum(sin, Real[]; init=1.0)  # bien, ya que la salida de sin es <= 1
1.0
```
