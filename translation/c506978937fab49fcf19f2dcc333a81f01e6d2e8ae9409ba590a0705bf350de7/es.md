```
argmin(f, domain)
```

Devuelve un valor `x` de `domain` para el cual `f(x)` es minimizado. Si hay múltiples valores mínimos para `f(x)`, se encontrará el primero.

`domain` debe ser un iterable no vacío.

`NaN` se trata como menor que todos los demás valores excepto `missing`.

!!! compat "Julia 1.7"
    Este método requiere Julia 1.7 o posterior.


Véase también [`argmax`](@ref), [`findmin`](@ref).

# Ejemplos

```jldoctest
julia> argmin(sign, -10:5)
-10

julia> argmin(x -> -x^3 + x^2 - 10, -5:5)
5

julia> argmin(acos, 0:0.1:1)
1.0
```
