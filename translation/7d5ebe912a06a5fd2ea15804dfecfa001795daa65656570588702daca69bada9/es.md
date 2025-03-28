```
__precompile__(isprecompilable::Bool)
```

Especifica si el archivo que llama a esta función es precompilable, con un valor predeterminado de `true`. Si un módulo o archivo *no* es seguro para la precompilación, debe llamar a `__precompile__(false)` para lanzar un error si Julia intenta precompilarlo.
