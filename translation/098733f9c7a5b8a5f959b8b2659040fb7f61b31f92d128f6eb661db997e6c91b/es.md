```
checkindex(Bool, inds::AbstractUnitRange, index)
```

Devuelve `true` si el `index` dado está dentro de los límites de `inds`. Los tipos personalizados que deseen comportarse como índices para todos los arreglos pueden extender este método para proporcionar una implementación de verificación de límites especializada.

Ver también [`checkbounds`](@ref).

# Ejemplos

```jldoctest
julia> checkindex(Bool, 1:20, 8)
true

julia> checkindex(Bool, 1:20, 21)
false
```
