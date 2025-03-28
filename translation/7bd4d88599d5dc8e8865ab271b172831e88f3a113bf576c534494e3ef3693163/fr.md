```
bunchkaufman!(A, rook::Bool=false; check = true) -> BunchKaufman
```

`bunchkaufman!` est identique à [`bunchkaufman`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie.
