```
Slices{P,SM,AX,S,N} <: AbstractSlices{S,N}
```

Un `AbstractArray` de secciones en un array padre sobre dimensión(es) especificada(s), devolviendo vistas que seleccionan todos los datos de la(s) otra(s) dimensión(es).

Estos deberían ser construidos típicamente por [`eachslice`](@ref), [`eachcol`](@ref) o [`eachrow`](@ref).

[`parent(s::Slices)`](@ref) devolverá el array padre.
