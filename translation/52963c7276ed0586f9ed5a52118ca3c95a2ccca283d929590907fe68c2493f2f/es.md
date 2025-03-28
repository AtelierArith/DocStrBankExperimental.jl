```
methods(f, [types], [module])
```

Devuelve la tabla de métodos para `f`.

Si se especifica `types`, devuelve un array de métodos cuyas tipos coinciden. Si se especifica `module`, devuelve un array de métodos definidos en ese módulo. También se puede especificar una lista de módulos como un array.

!!! compat "Julia 1.4"
    Se requiere al menos Julia 1.4 para especificar un módulo.


Véase también: [`which`](@ref), [`@which`](@ref Main.InteractiveUtils.@which) y [`methodswith`](@ref Main.InteractiveUtils.methodswith).
