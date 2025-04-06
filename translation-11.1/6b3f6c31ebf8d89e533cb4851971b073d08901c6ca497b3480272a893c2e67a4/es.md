```
mapreduce(f, op, itrs...; [init])
```

Aplica la función `f` a cada elemento(s) en `itrs`, y luego reduce el resultado usando la función binaria `op`. Si se proporciona, `init` debe ser un elemento neutro para `op` que se devolverá para colecciones vacías. No se especifica si `init` se utiliza para colecciones no vacías. En general, será necesario proporcionar `init` para trabajar con colecciones vacías.

[`mapreduce`](@ref) es funcionalmente equivalente a llamar a `reduce(op, map(f, itr); init=init)`, pero en general se ejecutará más rápido ya que no es necesario crear una colección intermedia. Consulta la documentación de [`reduce`](@ref) y [`map`](@ref).

!!! compat "Julia 1.2"
    `mapreduce` con múltiples iteradores requiere Julia 1.2 o posterior.


# Ejemplos

```jldoctest
julia> mapreduce(x->x^2, +, [1:3;]) # == 1 + 4 + 9
14
```

La asociatividad de la reducción depende de la implementación. Además, algunas implementaciones pueden reutilizar el valor de retorno de `f` para elementos que aparecen múltiples veces en `itr`. Usa [`mapfoldl`](@ref) o [`mapfoldr`](@ref) en su lugar para garantizar la asociatividad izquierda o derecha y la invocación de `f` para cada valor.
