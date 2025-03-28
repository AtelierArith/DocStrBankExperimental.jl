```
Slices{P,SM,AX,S,N} <: AbstractSlices{S,N}
```

Ein `AbstractArray` von Schnitten in ein übergeordnete Array über die angegebenen Dimension(en), das Ansichten zurückgibt, die alle Daten aus den anderen Dimension(en) auswählen.

Diese sollten typischerweise durch [`eachslice`](@ref), [`eachcol`](@ref) oder [`eachrow`](@ref) erstellt werden.

[`parent(s::Slices)`](@ref) gibt das übergeordnete Array zurück.
