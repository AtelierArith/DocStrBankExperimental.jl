```
arg_isdir(f::Function, arg::AbstractString) -> f(arg)
```

La función `arg_isdir` toma `arg`, que debe ser la ruta a un directorio existente (se genera un error de lo contrario) y pasa esa ruta a `f`, devolviendo finalmente el resultado de `f(arg)`. Esta es definitivamente la herramienta menos útil ofrecida por `ArgTools` y existe principalmente por simetría con `arg_mkdir` y para proporcionar mensajes de error consistentes.
