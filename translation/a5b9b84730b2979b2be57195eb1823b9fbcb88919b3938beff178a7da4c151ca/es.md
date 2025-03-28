```
detect_ambiguities(mod1, mod2...; recursive=false,
                                  ambiguous_bottom=false,
                                  allowed_undefineds=nothing)
```

Devuelve un vector de pares `(Method,Method)` de métodos ambiguos definidos en los módulos especificados. Usa `recursive=true` para probar en todos los submódulos.

`ambiguous_bottom` controla si se incluyen las ambigüedades provocadas solo por parámetros de tipo `Union{}`; en la mayoría de los casos probablemente querrás establecer esto en `false`. Consulta [`Base.isambiguous`](@ref).

Consulta [`Test.detect_unbound_args`](@ref) para una explicación de `allowed_undefineds`.

!!! compat "Julia 1.8"
    `allowed_undefineds` requiere al menos Julia 1.8.

