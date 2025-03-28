```
keys(m::RegexMatch) -> Vector
```

Devuelve un vector de claves para todos los grupos de captura de la expresión regular subyacente. Una clave se incluye incluso si el grupo de captura no coincide. Es decir, `idx` estará en el valor de retorno incluso si `m[idx] == nothing`.

Los grupos de captura sin nombre tendrán claves enteras correspondientes a su índice. Los grupos de captura con nombre tendrán claves de cadena.

!!! compat "Julia 1.7"
    Este método se agregó en Julia 1.7


# Ejemplos

```jldoctest
julia> keys(match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30"))
3-element Vector{Any}:
  "hour"
  "minute"
 3
```
