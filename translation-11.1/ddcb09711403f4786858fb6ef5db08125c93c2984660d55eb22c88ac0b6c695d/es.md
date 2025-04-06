```
subtipos(T::DataType)
```

Devuelve una lista de subtipos inmediatos del tipo de dato `T`. Ten en cuenta que se incluyen todos los subtipos actualmente cargados, incluidos aquellos que no son visibles en el módulo actual.

Consulta también [`supertype`](@ref), [`supertypes`](@ref), [`methodswith`](@ref).

# Ejemplos

```jldoctest
julia> subtipos(Integer)
3-element Vector{Any}:
 Bool
 Signed
 Unsigned
```
