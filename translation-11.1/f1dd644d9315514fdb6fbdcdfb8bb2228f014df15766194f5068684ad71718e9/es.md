```
LibGit2.StatusOptions
```

Opciones para controlar cómo `git_status_foreach_ext()` emitirá callbacks. Coincide con la estructura [`git_status_opt_t`](https://libgit2.org/libgit2/#HEAD/type/git_status_opt_t).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `show`: una bandera para qué archivos examinar y en qué orden. El valor predeterminado es `Consts.STATUS_SHOW_INDEX_AND_WORKDIR`.
  * `flags`: banderas para controlar cualquier callback utilizado en una llamada de estado.
  * `pathspec`: un array de rutas a utilizar para la coincidencia de rutas. El comportamiento de la coincidencia de rutas variará dependiendo de los valores de `show` y `flags`.
  * El `baseline` es el árbol que se utilizará para la comparación con el directorio de trabajo y el índice; por defecto es HEAD.
