```
LibGit2.DiffFile
```

Beschreibung einer Seite eines Deltas. Entspricht der [`git_diff_file`](https://libgit2.org/libgit2/#HEAD/type/git_diff_file) Struktur.

Die Felder repräsentieren:

  * `id`: der [`GitHash`](@ref) des Elements im Diff. Wenn das Element auf dieser Seite des Diffs leer ist (zum Beispiel, wenn das Diff die Entfernung einer Datei betrifft), wird dies `GitHash(0)` sein.
  * `path`: ein mit `NULL` terminiertem Pfad zum Element relativ zum Arbeitsverzeichnis des Repositories.
  * `size`: die Größe des Elements in Bytes.
  * `flags`: eine Kombination der [`git_diff_flag_t`](https://libgit2.org/libgit2/#HEAD/type/git_diff_flag_t) Flags. Das `i`te Bit dieser Ganzzahl setzt das `i`te Flag.
  * `mode`: der [`stat`](@ref) Modus für das Element.
  * `id_abbrev`: nur vorhanden in LibGit2-Versionen, die neuer oder gleich `0.25.0` sind. Die Länge des `id`-Feldes, wenn es mit [`string`](@ref) konvertiert wird. Üblicherweise gleich `OID_HEXSZ` (40).
