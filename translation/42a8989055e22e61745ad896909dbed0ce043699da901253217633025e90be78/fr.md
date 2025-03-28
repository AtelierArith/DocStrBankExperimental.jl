```
Slices{P,SM,AX,S,N} <: AbstractSlices{S,N}
```

Un `AbstractArray` de tranches dans un tableau parent sur des dimensions spécifiées, retournant des vues qui sélectionnent toutes les données des autres dimensions.

Celles-ci devraient généralement être construites par [`eachslice`](@ref), [`eachcol`](@ref) ou [`eachrow`](@ref).

[`parent(s::Slices)`](@ref) renverra le tableau parent.
