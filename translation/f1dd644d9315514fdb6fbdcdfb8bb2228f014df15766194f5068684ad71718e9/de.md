```
LibGit2.StatusOptions
```

Optionen zur Steuerung, wie `git_status_foreach_ext()` Rückrufe ausführt. Entspricht der [`git_status_opt_t`](https://libgit2.org/libgit2/#HEAD/type/git_status_opt_t) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Zurzeit immer `1`.
  * `show`: ein Flag, für welche Dateien untersucht werden sollen und in welcher Reihenfolge. Der Standardwert ist `Consts.STATUS_SHOW_INDEX_AND_WORKDIR`.
  * `flags`: Flags zur Steuerung von Rückrufen, die in einem Statusaufruf verwendet werden.
  * `pathspec`: ein Array von Pfaden, die für die Pfadübereinstimmung verwendet werden sollen. Das Verhalten der Pfadübereinstimmung variiert je nach den Werten von `show` und `flags`.
  * Der `baseline` ist der Baum, der für den Vergleich mit dem Arbeitsverzeichnis und dem Index verwendet wird; standardmäßig HEAD.
