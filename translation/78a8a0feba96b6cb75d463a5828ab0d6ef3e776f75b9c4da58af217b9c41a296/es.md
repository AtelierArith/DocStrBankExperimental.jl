```
startswith(prefix)
```

Crea una función que verifica si su argumento comienza con `prefix`, es decir, una función equivalente a `y -> startswith(y, prefix)`.

La función devuelta es de tipo `Base.Fix2{typeof(startswith)}`, que se puede usar para implementar métodos especializados.

!!! compat "Julia 1.5"
    El argumento único `startswith(prefix)` requiere al menos Julia 1.5.


# Ejemplos

```jldoctest
julia> startswith("Julia")("JuliaLang")
true

julia> startswith("Julia")("Ends with Julia")
false
```
