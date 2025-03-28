```
bunchkaufman!(A, rook::Bool=false; check = true) -> BunchKaufman
```

`bunchkaufman!` es lo mismo que [`bunchkaufman`](@ref), pero ahorra espacio al sobrescribir la entrada `A`, en lugar de crear una copia.
