```
eigen!(A; permute, scale, sortby)
eigen!(A, B; sortby)
```

Igual que [`eigen`](@ref), pero ahorra espacio al sobrescribir la entrada `A` (y `B`), en lugar de crear una copia.
