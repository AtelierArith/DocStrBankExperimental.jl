```
reenable_sigint(f::Function)
```

Vuelve a habilitar el controlador de Ctrl-C durante la ejecución de una función. Revierte temporalmente el efecto de [`disable_sigint`](@ref).
