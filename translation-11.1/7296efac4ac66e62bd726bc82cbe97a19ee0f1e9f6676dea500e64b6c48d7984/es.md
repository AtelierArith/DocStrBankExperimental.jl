```
LibGit2.DiffOptionsStruct
```

Coincide con la estructura [`git_diff_options`](https://libgit2.org/libgit2/#HEAD/type/git_diff_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `flags`: banderas que controlan qué archivos aparecerán en la diferencia. Por defecto es `DIFF_NORMAL`.
  * `ignore_submodules`: si se deben considerar los archivos en submódulos o no. Por defecto es `SUBMODULE_IGNORE_UNSPECIFIED`, lo que significa que la configuración del submódulo controlará si aparece en la diferencia o no.
  * `pathspec`: ruta a los archivos que se incluirán en la diferencia. El valor por defecto es usar todos los archivos en el repositorio.
  * `notify_cb`: callback opcional que notificará al usuario sobre cambios en la diferencia a medida que se agreguen deltas de archivos.
  * `progress_cb`: callback opcional que mostrará el progreso de la diferencia. Solo es relevante en versiones de libgit2 al menos tan nuevas como 0.24.0.
  * `payload`: la carga útil que se pasará a `notify_cb` y `progress_cb`.
  * `context_lines`: el número de líneas *sin cambios* utilizadas para definir los bordes de un hunk. Este también es el número de líneas que se mostrarán antes/después de un hunk para proporcionar contexto. El valor por defecto es 3.
  * `interhunk_lines`: el número máximo de líneas *sin cambios* *entre* dos hunks separados permitidos antes de que los hunks se combinen. El valor por defecto es 0.
  * `id_abbrev`: establece la longitud del [`GitHash`](@ref) abreviado a imprimir. El valor por defecto es `7`.
  * `max_size`: el tamaño máximo de archivo de un blob. Por encima de este tamaño, se tratará como un blob binario. El valor por defecto es 512 MB.
  * `old_prefix`: el directorio de archivos virtual en el que colocar archivos antiguos en un lado de la diferencia. El valor por defecto es `"a"`.
  * `new_prefix`: el directorio de archivos virtual en el que colocar archivos nuevos en un lado de la diferencia. El valor por defecto es `"b"`.
