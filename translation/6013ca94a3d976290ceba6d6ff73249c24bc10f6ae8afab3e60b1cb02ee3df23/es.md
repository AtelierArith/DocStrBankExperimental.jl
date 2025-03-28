```
add!(repo::GitRepo, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
add!(idx::GitIndex, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
```

Agrega todos los archivos con rutas especificadas por `files` al índice `idx` (o al índice del `repo`). Si el archivo ya existe, la entrada del índice se actualizará. Si el archivo no existe ya, se añadirá nuevo al índice. `files` puede contener patrones glob que serán expandido y cualquier archivo que coincida será añadido (a menos que `INDEX_ADD_DISABLE_PATHSPEC_MATCH` esté configurado, ver más abajo). Si un archivo ha sido ignorado (en `.gitignore` o en la configuración), *no se añadirá*, *a menos que* ya esté siendo rastreado en el índice, en cuyo caso *se actualizará*. El argumento clave `flags` es un conjunto de banderas de bits que controlan el comportamiento con respecto a los archivos ignorados:

  * `Consts.INDEX_ADD_DEFAULT` - por defecto, descrito arriba.
  * `Consts.INDEX_ADD_FORCE` - desestimar las reglas de ignorar existentes y forzar la adición del archivo al índice incluso si ya está ignorado.
  * `Consts.INDEX_ADD_CHECK_PATHSPEC` - no se puede usar al mismo tiempo que `INDEX_ADD_FORCE`. Verifica que cada archivo en `files` que existe en el disco no esté en la lista de ignorados. Si uno de los archivos *está* ignorado, la función devolverá `EINVALIDSPEC`.
  * `Consts.INDEX_ADD_DISABLE_PATHSPEC_MATCH` - desactivar la coincidencia glob, y solo añadir archivos al índice que coincidan exactamente con las rutas especificadas en `files`.
