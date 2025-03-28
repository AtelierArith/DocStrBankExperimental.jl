```
Val(c)
```

Devuelve `Val{c}()`, que no contiene datos en tiempo de ejecución. Tipos como este se pueden usar para pasar la información entre funciones a través del valor `c`, que debe ser un valor `isbits` o un `Symbol`. La intención de esta construcción es poder despachar sobre constantes directamente (en tiempo de compilación) sin tener que probar el valor de la constante en tiempo de ejecución.

# Ejemplos

```jldoctest
julia> f(::Val{true}) = "Good"
f (función genérica con 1 método)

julia> f(::Val{false}) = "Bad"
f (función genérica con 2 métodos)

julia> f(Val(true))
"Good"
```
