```
finish(ts::AbstractTestSet)
```

Realiza cualquier procesamiento final necesario para el conjunto de pruebas dado. Esto es llamado por la infraestructura `@testset` después de que se ejecuta un bloque de prueba.

Los subtipos personalizados de `AbstractTestSet` deben llamar a `record` en su padre (si lo hay) para agregarse al árbol de resultados de pruebas. Esto podría implementarse como:

```julia
if get_testset_depth() != 0
    # Adjuntar este conjunto de pruebas al conjunto de pruebas padre
    parent_ts = get_testset()
    record(parent_ts, self)
    return self
end
```
