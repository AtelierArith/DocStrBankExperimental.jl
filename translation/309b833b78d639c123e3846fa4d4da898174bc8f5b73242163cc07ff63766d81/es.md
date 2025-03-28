```
record(ts::AbstractTestSet, res::Result)
```

Registra un resultado en un conjunto de pruebas. Esta función es llamada por la infraestructura `@testset` cada vez que se completa un macro `@test` contenido, y se le da el resultado de la prueba (que podría ser un `Error`). Esto también se llamará con un `Error` si se lanza una excepción dentro del bloque de prueba pero fuera de un contexto `@test`.
