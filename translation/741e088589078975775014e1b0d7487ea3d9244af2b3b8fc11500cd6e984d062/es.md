```
endswith(suffix)
```

Crea una función que verifica si su argumento termina con `suffix`, es decir, una función equivalente a `y -> endswith(y, suffix)`.

La función devuelta es de tipo `Base.Fix2{typeof(endswith)}`, que se puede usar para implementar métodos especializados.

!!! compat "Julia 1.5"
    El argumento único `endswith(suffix)` requiere al menos Julia 1.5.


# Ejemplos

```jldoctest
julia> endswith("Julia")("Ends with Julia")
true

julia> endswith("Julia")("JuliaLang")
false
```
