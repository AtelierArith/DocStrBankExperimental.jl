```
WeakRef(x)
```

`w = WeakRef(x)` construye una [referencia débil](https://es.wikipedia.org/wiki/Referencia_d%C3%A9bil) al valor de Julia `x`: aunque `w` contiene una referencia a `x`, no impide que `x` sea recolectado por el recolector de basura. `w.value` es `x` (si `x` no ha sido recolectado por el recolector de basura aún) o `nothing` (si `x` ha sido recolectado por el recolector de basura).

```jldoctest
julia> x = "a string"
"a string"

julia> w = WeakRef(x)
WeakRef("a string")

julia> GC.gc()

julia> w           # se mantiene una referencia a través de `x`
WeakRef("a string")

julia> x = nothing # limpiar referencia

julia> GC.gc()

julia> w
WeakRef(nothing)
```
