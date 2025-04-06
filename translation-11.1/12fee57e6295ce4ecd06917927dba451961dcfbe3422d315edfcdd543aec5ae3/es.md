```
LibGit2.BlameOptions
```

Coincide con la estructura [`git_blame_options`](https://libgit2.org/libgit2/#HEAD/type/git_blame_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `flags`: uno de `Consts.BLAME_NORMAL` o `Consts.BLAME_FIRST_PARENT` (los otros flags de blame aún no están implementados por libgit2).
  * `min_match_characters`: el número mínimo de caracteres *alfanuméricos* que deben cambiar en un commit para que el cambio se asocie con ese commit. El valor predeterminado es 20. Solo tiene efecto si se utiliza uno de los flags `Consts.BLAME_*_COPIES`, que libgit2 aún no implementa.
  * `newest_commit`: el [`GitHash`](@ref) del commit más reciente desde el cual observar cambios.
  * `oldest_commit`: el [`GitHash`](@ref) del commit más antiguo desde el cual observar cambios.
  * `min_line`: la primera línea del archivo desde la cual comenzar a hacer blame. El valor predeterminado es `1`.
  * `max_line`: la última línea del archivo a la que hacer blame. El valor predeterminado es `0`, lo que significa la última línea del archivo.
