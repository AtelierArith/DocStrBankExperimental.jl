```
AbstractRange{T} <: AbstractVector{T}
```

Supertipo para rangos lineales con elementos del tipo `T`. [`UnitRange`](@ref), [`LinRange`](@ref) y otros tipos son subtipos de esto.

Todos los subtipos deben definir [`step`](@ref). Por lo tanto, [`LogRange`](@ref Base.LogRange) no es un subtipo de `AbstractRange`.
