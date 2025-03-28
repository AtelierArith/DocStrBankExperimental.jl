```
LibGit2.DescribeOptions
```

Coincide con la estructura [`git_describe_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `max_candidates_tags`: considera este número de las etiquetas más recientes en `refs/tags` para describir un commit. Por defecto es 10 (por lo que se examinarían las 10 etiquetas más recientes para ver si describen un commit).
  * `describe_strategy`: si considerar todas las entradas en `refs/tags` (equivalente a `git-describe --tags`) o todas las entradas en `refs/` (equivalente a `git-describe --all`). El valor predeterminado es mostrar solo etiquetas anotadas. Si se pasa `Consts.DESCRIBE_TAGS`, se considerarán todas las etiquetas, anotadas o no. Si se pasa `Consts.DESCRIBE_ALL`, se considerará cualquier ref en `refs/`.
  * `pattern`: solo considera etiquetas que coincidan con `pattern`. Soporta expansión glob.
  * `only_follow_first_parent`: al encontrar la distancia desde una referencia coincidente al objeto descrito, solo considera la distancia desde el primer padre.
  * `show_commit_oid_as_fallback`: si no se puede encontrar una referencia coincidente que describa un commit, muestra el [`GitHash`](@ref) del commit en lugar de lanzar un error (el comportamiento predeterminado).
