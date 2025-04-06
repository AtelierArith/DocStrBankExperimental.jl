```
with_warn(f::Function, ::Type{T}, args...)
```

Función auxiliar de gestión de recursos. Aplica `f` a `args`, primero construyendo una instancia del tipo `T` a partir de `args`. Asegura que se llame a `close` en el objeto resultante después de que `f` devuelva exitosamente o lance un error. Asegura que los recursos de git asignados se finalicen tan pronto como ya no sean necesarios. Si `f` lanza un error, se muestra una advertencia que contiene el error. ```
