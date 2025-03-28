```
SubArray{T,N,P,I,L} <: AbstractArray{T,N}
```

`N`-dimensionale Ansicht in ein übergeordnetes Array (vom Typ `P`) mit einem Elementtyp `T`, eingeschränkt durch ein Tupel von Indizes (vom Typ `I`). `L` ist wahr für Typen, die schnelles lineares Indizieren unterstützen, und `falsch` andernfalls.

Konstruiere `SubArray`s mit der [`view`](@ref) Funktion.
