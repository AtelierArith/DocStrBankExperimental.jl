```
string(xs...)
```

Crea una cadena a partir de cualquier valor utilizando la función [`print`](@ref).

`string` no debería definirse directamente. En su lugar, define un método `print(io::IO, x::MyType)`. Si `string(x)` para un cierto tipo necesita ser altamente eficiente, entonces puede tener sentido agregar un método a `string` y definir `print(io::IO, x::MyType) = print(io, string(x))` para asegurar que las funciones sean consistentes.

Ver también: [`String`](@ref), [`repr`](@ref), [`sprint`](@ref), [`show`](@ref @show).

# Ejemplos

```jldoctest
julia> string("a", 1, true)
"a1true"
```
