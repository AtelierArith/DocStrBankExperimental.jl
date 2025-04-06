```
LibGit2.DescribeFormatOptions
```

Entspricht der [`git_describe_format_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_format_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Zurzeit immer `1`.
  * `abbreviated_size`: untere Grenze für die Größe des abgekürzten `GitHash`, die verwendet werden soll, standardmäßig `7`.
  * `always_use_long_format`: auf `1` setzen, um das lange Format für Strings zu verwenden, auch wenn ein kurzes Format verwendet werden kann.
  * `dirty_suffix`: Wenn gesetzt, wird dies am Ende des Beschreibungsstrings angehängt, wenn das [`workdir`](@ref) schmutzig ist.
