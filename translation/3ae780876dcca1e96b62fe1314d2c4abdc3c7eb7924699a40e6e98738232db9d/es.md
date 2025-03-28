```
with(f::Function, obj)
```

Función auxiliar de gestión de recursos. Aplica `f` a `obj`, asegurándose de llamar a `close` en `obj` después de que `f` devuelva con éxito o lance un error. Asegura que los recursos de git asignados se finalicen tan pronto como ya no sean necesarios.
