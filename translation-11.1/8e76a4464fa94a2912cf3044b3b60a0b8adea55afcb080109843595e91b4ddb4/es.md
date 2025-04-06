```
LibGit2.DiffFile
```

Descripción de un lado de un delta. Coincide con la estructura [`git_diff_file`](https://libgit2.org/libgit2/#HEAD/type/git_diff_file).

Los campos representan:

  * `id`: el [`GitHash`](@ref) del elemento en la diferencia. Si el elemento está vacío en este lado de la diferencia (por ejemplo, si la diferencia es de la eliminación de un archivo), esto será `GitHash(0)`.
  * `path`: una ruta terminada en `NULL` al elemento relativa al directorio de trabajo del repositorio.
  * `size`: el tamaño del elemento en bytes.
  * `flags`: una combinación de las banderas [`git_diff_flag_t`](https://libgit2.org/libgit2/#HEAD/type/git_diff_flag_t). El bit `i` de este entero establece la bandera `i`.
  * `mode`: el modo [`stat`](@ref) para el elemento.
  * `id_abbrev`: solo presente en versiones de LibGit2 más nuevas o iguales a `0.25.0`. La longitud del campo `id` cuando se convierte usando [`string`](@ref). Generalmente igual a `OID_HEXSZ` (40).
