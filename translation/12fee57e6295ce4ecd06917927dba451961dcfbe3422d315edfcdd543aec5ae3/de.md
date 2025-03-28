```
LibGit2.BlameOptions
```

Entspricht der [`git_blame_options`](https://libgit2.org/libgit2/#HEAD/type/git_blame_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Für jetzt immer `1`.
  * `flags`: eines von `Consts.BLAME_NORMAL` oder `Consts.BLAME_FIRST_PARENT` (die anderen Blame-Flags sind von libgit2 noch nicht implementiert).
  * `min_match_characters`: die minimale Anzahl von *alphanumerischen* Zeichen, die sich in einem Commit ändern müssen, damit die Änderung mit diesem Commit assoziiert wird. Der Standardwert ist 20. Hat nur Wirkung, wenn eines der `Consts.BLAME_*_COPIES`-Flags verwendet wird, die libgit2 noch nicht implementiert.
  * `newest_commit`: der [`GitHash`](@ref) des neuesten Commits, von dem aus Änderungen betrachtet werden sollen.
  * `oldest_commit`: der [`GitHash`](@ref) des ältesten Commits, von dem aus Änderungen betrachtet werden sollen.
  * `min_line`: die erste Zeile der Datei, von der aus mit dem Blamen begonnen werden soll. Der Standardwert ist `1`.
  * `max_line`: die letzte Zeile der Datei, die geblamet werden soll. Der Standardwert ist `0`, was die letzte Zeile der Datei bedeutet.
