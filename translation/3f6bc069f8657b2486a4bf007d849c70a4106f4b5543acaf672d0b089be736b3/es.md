```
repr(x; context=nothing)
```

Crea una cadena a partir de cualquier valor utilizando la función [`show`](@ref). No debes agregar métodos a `repr`; en su lugar, define un método `show`.

El argumento de palabra clave opcional `context` se puede establecer en un par `:key=>value`, una tupla de pares `:key=>value`, o un objeto `IO` o [`IOContext`](@ref) cuyos atributos se utilizan para el flujo de I/O pasado a `show`.

Ten en cuenta que `repr(x)` suele ser similar a cómo se ingresaría el valor de `x` en Julia. También consulta [`repr(MIME("text/plain"), x)`](@ref) para devolver en su lugar una versión "bien presentada" de `x` diseñada más para el consumo humano, equivalente a la visualización de `x` en el REPL.

!!! compat "Julia 1.7"
    Pasar una tupla al argumento de palabra clave `context` requiere Julia 1.7 o posterior.


# Ejemplos

```jldoctest
julia> repr(1)
"1"

julia> repr(zeros(3))
"[0.0, 0.0, 0.0]"

julia> repr(big(1/3))
"0.333333333333333314829616256247390992939472198486328125"

julia> repr(big(1/3), context=:compact => true)
"0.333333"
```
