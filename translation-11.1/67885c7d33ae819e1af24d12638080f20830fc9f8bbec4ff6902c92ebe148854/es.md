```
LibGit2.DescribeFormatOptions
```

Coincide con la estructura [`git_describe_format_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_format_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `abbreviated_size`: límite inferior en el tamaño del `GitHash` abreviado a utilizar, que por defecto es `7`.
  * `always_use_long_format`: establecer en `1` para usar el formato largo para cadenas incluso si se puede usar un formato corto.
  * `dirty_suffix`: si se establece, esto se añadirá al final de la cadena de descripción si el [`workdir`](@ref) está sucio.
