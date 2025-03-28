```
which(f, types)
```

Devuelve el método de `f` (un objeto `Method`) que se llamaría para argumentos de los tipos dados `types`.

Si `types` es un tipo abstracto, se devuelve el método que sería llamado por `invoke`.

Véase también: [`parentmodule`](@ref), [`@which`](@ref Main.InteractiveUtils.@which), y [`@edit`](@ref Main.InteractiveUtils.@edit).
