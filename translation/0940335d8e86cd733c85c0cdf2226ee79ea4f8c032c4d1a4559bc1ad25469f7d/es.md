```
readavailable(stream)
```

Lee los datos en búfer disponibles de un flujo. La entrada/salida real se realiza solo si no se ha almacenado en búfer ningún dato. El resultado es un `Vector{UInt8}`.

!!! warning
    La cantidad de datos devueltos depende de la implementación; por ejemplo, puede depender de la elección interna del tamaño del búfer. Otras funciones como [`read`](@ref) deberían usarse generalmente en su lugar.

