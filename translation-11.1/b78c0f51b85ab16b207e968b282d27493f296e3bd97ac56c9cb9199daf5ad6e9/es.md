```
remoteref_id(r::AbstractRemoteRef) -> RRID
```

`Future`s y `RemoteChannel`s se identifican por campos:

  * `where` - se refiere al nodo donde el objeto/almacenamiento subyacente al que se refiere la referencia realmente existe.
  * `whence` - se refiere al nodo desde el cual se creó la referencia remota. Tenga en cuenta que esto es diferente del nodo donde el objeto subyacente al que se refiere realmente existe. Por ejemplo, llamar a `RemoteChannel(2)` desde el proceso maestro resultaría en un valor de `where` de 2 y un valor de `whence` de 1.
  * `id` es único entre todas las referencias creadas desde el trabajador especificado por `whence`.

Tomados en conjunto, `whence` e `id` identifican de manera única una referencia entre todos los trabajadores.

`remoteref_id` es una API de bajo nivel que devuelve un objeto `RRID` que envuelve los valores de `whence` e `id` de una referencia remota.
