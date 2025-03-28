```
prod(f, itr; [init])
```

Devuelve el producto de `f` aplicado a cada elemento de `itr`.

El tipo de retorno es `Int` para enteros con signo de menos del tamaño de palabra del sistema, y `UInt` para enteros sin signo de menos del tamaño de palabra del sistema. Para todos los demás argumentos, se encuentra un tipo de retorno común al que se promueven todos los argumentos.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser la identidad multiplicativa (es decir, uno) ya que no está especificado si `init` se utiliza para colecciones no vacías.

!!! compat "Julia 1.6"
    El argumento clave `init` requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> prod(abs2, [2; 3; 4])
576
```
