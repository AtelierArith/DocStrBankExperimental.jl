```
LibGit2.StatusEntry
```

Proporciona las diferencias entre el archivo tal como existe en HEAD y el índice, y proporciona las diferencias entre el índice y el directorio de trabajo. Coincide con la estructura `git_status_entry`.

Los campos representan:

  * `status`: contiene las banderas de estado para el archivo, indicando si está actual o ha sido cambiado de alguna manera en el índice o en el árbol de trabajo.
  * `head_to_index`: un puntero a un [`DiffDelta`](@ref) que encapsula la(s) diferencia(s) entre el archivo tal como existe en HEAD y en el índice.
  * `index_to_workdir`: un puntero a un `DiffDelta` que encapsula la(s) diferencia(s) entre el archivo tal como existe en el índice y en el [`workdir`](@ref).
