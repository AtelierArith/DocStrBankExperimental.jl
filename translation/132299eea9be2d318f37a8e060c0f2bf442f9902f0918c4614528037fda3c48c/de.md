```
LibGit2.StatusEntry
```

Bereitstellung der Unterschiede zwischen der Datei, wie sie in HEAD existiert, und dem Index, sowie der Unterschiede zwischen dem Index und dem Arbeitsverzeichnis. Entspricht der Struktur `git_status_entry`.

Die Felder repräsentieren:

  * `status`: enthält die Statusflags für die Datei, die angeben, ob sie aktuell ist oder in irgendeiner Weise im Index oder Arbeitsbaum geändert wurde.
  * `head_to_index`: ein Zeiger auf ein [`DiffDelta`](@ref), das die Unterschiede zwischen der Datei, wie sie in HEAD existiert, und im Index kapselt.
  * `index_to_workdir`: ein Zeiger auf ein `DiffDelta`, das die Unterschiede zwischen der Datei, wie sie im Index existiert, und im [`workdir`](@ref) kapselt.
