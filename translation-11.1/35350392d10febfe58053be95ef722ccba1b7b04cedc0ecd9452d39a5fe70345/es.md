```
LibGit2.CheckoutOptions
```

Coincide con la estructura [`git_checkout_options`](https://libgit2.org/libgit2/#HEAD/type/git_checkout_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `checkout_strategy`: determina cómo manejar los conflictos y si forzar la checkout/recrear archivos faltantes.
  * `disable_filters`: si es distinto de cero, no aplicar filtros como CLRF (para convertir los saltos de línea de archivos entre UNIX y DOS).
  * `dir_mode`: modo de lectura/escritura/acceso para cualquier directorio involucrado en la checkout. El valor predeterminado es `0755`.
  * `file_mode`: modo de lectura/escritura/acceso para cualquier archivo involucrado en la checkout. El valor predeterminado es `0755` o `0644`, dependiendo del blob.
  * `file_open_flags`: banderas de bits utilizadas para abrir cualquier archivo durante la checkout.
  * `notify_flags`: Banderas sobre qué tipo de conflictos se debe notificar al usuario.
  * `notify_cb`: Una función de callback opcional para notificar al usuario si ocurre un conflicto de checkout. Si esta función devuelve un valor distinto de cero, la checkout será cancelada.
  * `notify_payload`: Carga útil para la función de callback de notificación.
  * `progress_cb`: Una función de callback opcional para mostrar el progreso de la checkout.
  * `progress_payload`: Carga útil para el callback de progreso.
  * `paths`: Si no está vacío, describe qué rutas buscar durante la checkout. Si está vacío, la checkout ocurrirá sobre todos los archivos en el repositorio.
  * `baseline`: Contenido esperado del [`workdir`](@ref), capturado en un (puntero a un) [`GitTree`](@ref). Por defecto, es el estado del árbol en HEAD.
  * `baseline_index`: Contenido esperado del [`workdir`](@ref), capturado en un (puntero a un) `GitIndex`. Por defecto, es el estado del índice en HEAD.
  * `target_directory`: Si no está vacío, checkout a este directorio en lugar del `workdir`.
  * `ancestor_label`: En caso de conflictos, el nombre del lado del ancestro común.
  * `our_label`: En caso de conflictos, el nombre de "nuestro" lado.
  * `their_label`: En caso de conflictos, el nombre de "su" lado.
  * `perfdata_cb`: Una función de callback opcional para mostrar datos de rendimiento.
  * `perfdata_payload`: Carga útil para el callback de rendimiento.
