```
mktemp(parent=tempdir(); cleanup=true) -> (path, io)
```

Devuelve `(path, io)`, donde `path` es la ruta de un nuevo archivo temporal en `parent` y `io` es un objeto de archivo abierto para esta ruta. La opción `cleanup` controla si el archivo temporal se elimina automáticamente cuando el proceso finaliza.

!!! compat "Julia 1.3"
    El argumento de palabra clave `cleanup` se agregó en Julia 1.3. Relacionado con esto, a partir de 1.3, Julia eliminará las rutas temporales creadas por `mktemp` cuando el proceso de Julia finalice, a menos que `cleanup` se establezca explícitamente en `false`.

