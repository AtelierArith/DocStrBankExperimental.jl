```
eigvals!(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> values
```

Igual que [`eigvals`](@ref), pero ahorra espacio al sobrescribir la entrada `A`, en lugar de crear una copia. `irange` es un rango de *índices* de valores propios a buscar; por ejemplo, los valores propios del 2º al 8º.
