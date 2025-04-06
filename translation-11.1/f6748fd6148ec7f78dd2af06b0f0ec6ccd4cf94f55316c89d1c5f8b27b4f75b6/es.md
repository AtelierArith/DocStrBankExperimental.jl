```
addenv(command::Cmd, env...; inherit::Bool = true)
```

Fusiona nuevos mapeos de entorno en el objeto [`Cmd`](@ref) dado, devolviendo un nuevo objeto `Cmd`. Las claves duplicadas son reemplazadas. Si `command` no contiene ningún valor de entorno establecido ya, hereda el entorno actual en el momento de la llamada a `addenv()` si `inherit` es `true`. Las claves con valor `nothing` se eliminan del entorno.

Véase también [`Cmd`](@ref), [`setenv`](@ref), [`ENV`](@ref).

!!! compat "Julia 1.6"
    Esta función requiere Julia 1.6 o posterior.

