```
modifyproperty!(x, f::Symbol, op, v, order::Symbol=:not_atomic)
```

La sintaxis `@atomic op(x.f, v)` (y su equivalente `@atomic x.f op v`) devuelve `modifyproperty!(x, :f, op, v, :sequentially_consistent)`, donde el primer argumento debe ser una expresión `getproperty` y se modifica de manera atómica.

La invocación de `op(getproperty(x, f), v)` debe devolver un valor que se pueda almacenar en el campo `f` del objeto `x` por defecto. En particular, a diferencia del comportamiento predeterminado de [`setproperty!`](@ref Base.setproperty!), la función `convert` no se llama automáticamente.

Véase también [`modifyfield!`](@ref Core.modifyfield!) y [`setproperty!`](@ref Base.setproperty!).
