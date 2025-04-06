```
remote_do(f, id::Integer, args...; kwargs...) -> nothing
```

Ejecuta `f` en el trabajador `id` de forma asíncrona. A diferencia de [`remotecall`](@ref), no almacena el resultado de la computación, ni hay forma de esperar su finalización.

Una invocación exitosa indica que la solicitud ha sido aceptada para su ejecución en el nodo remoto.

Mientras que las llamadas consecutivas a `remotecall` al mismo trabajador se serializan en el orden en que se invocan, el orden de las ejecuciones en el trabajador remoto es indeterminado. Por ejemplo, `remote_do(f1, 2); remotecall(f2, 2); remote_do(f3, 2)` serializará la llamada a `f1`, seguida de `f2` y `f3` en ese orden. Sin embargo, no se garantiza que `f1` se ejecute antes que `f3` en el trabajador 2.

Cualquier excepción lanzada por `f` se imprime en [`stderr`](@ref) en el trabajador remoto.

Los argumentos de palabra clave, si los hay, se pasan a `f`.
