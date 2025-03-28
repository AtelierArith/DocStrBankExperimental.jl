```
LibGit2.DiffDelta
```

Beschreibung der Änderungen an einem Eintrag. Entspricht der [`git_diff_delta`](https://libgit2.org/libgit2/#HEAD/type/git_diff_delta) Struktur.

Die Felder repräsentieren:

  * `status`: Eines von `Consts.DELTA_STATUS`, das angibt, ob die Datei hinzugefügt/modifiziert/gelöscht wurde.
  * `flags`: Flags für das Delta und die Objekte auf jeder Seite. Bestimmt, ob die Datei(en) als binär/text behandelt werden, ob sie auf jeder Seite des Diffs existieren und ob die Objekt-IDs als korrekt bekannt sind.
  * `similarity`: Wird verwendet, um anzuzeigen, ob eine Datei umbenannt oder kopiert wurde.
  * `nfiles`: Die Anzahl der Dateien im Delta (zum Beispiel, wenn das Delta auf eine Submodul-Commit-ID angewendet wurde, kann es mehr als eine Datei enthalten).
  * `old_file`: Eine [`DiffFile`](@ref), die Informationen über die Datei(en) vor den Änderungen enthält.
  * `new_file`: Eine [`DiffFile`](@ref), die Informationen über die Datei(en) nach den Änderungen enthält.
