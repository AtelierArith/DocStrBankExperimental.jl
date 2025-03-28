```
poll_file(path::AbstractString, interval_s::Real=5.007, timeout_s::Real=-1) -> (previous::StatStruct, current)
```

Monitorea un archivo en busca de cambios mediante sondeos cada `interval_s` segundos hasta que ocurra un cambio o transcurran `timeout_s` segundos. El `interval_s` debe ser un período largo; el valor predeterminado es de 5.007 segundos.

Devuelve un par de objetos de estado `(previous, current)` cuando se detecta un cambio. El estado `previous` es siempre un `StatStruct`, pero puede tener todos los campos en cero (indicando que el archivo no existía previamente o no era accesible anteriormente).

El objeto de estado `current` puede ser un `StatStruct`, un `EOFError` (indicando que se agotó el tiempo de espera), o algún otro subtipo de `Exception` (si la operación `stat` falló - por ejemplo, si la ruta no existe).

Para determinar cuándo se modificó un archivo, compara `current isa StatStruct && mtime(prev) != mtime(current)` para detectar la notificación de cambios. Sin embargo, usar [`watch_file`](@ref) para esta operación es preferible, ya que es más confiable y eficiente, aunque en algunas situaciones puede no estar disponible.
