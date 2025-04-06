```
LibGit2.RebaseOperation
```

Beschreibt eine einzelne Anweisung/Operation, die während des Rebase ausgeführt werden soll. Entspricht der [`git_rebase_operation`](https://libgit2.org/libgit2/#HEAD/type/git_rebase_operation_t) Struktur.

Die Felder repräsentieren:

  * `optype`: der Typ der Rebase-Operation, die derzeit ausgeführt wird. Die Optionen sind:

      * `REBASE_OPERATION_PICK`: den betreffenden Commit cherry-picken.
      * `REBASE_OPERATION_REWORD`: den betreffenden Commit cherry-picken, aber seine Nachricht mit dem Prompt umschreiben.
      * `REBASE_OPERATION_EDIT`: den betreffenden Commit cherry-picken, aber dem Benutzer erlauben, den Inhalt des Commits und seine Nachricht zu bearbeiten.
      * `REBASE_OPERATION_SQUASH`: den betreffenden Commit in den vorherigen Commit squashen. Die Commit-Nachrichten der beiden Commits werden zusammengeführt.
      * `REBASE_OPERATION_FIXUP`: den betreffenden Commit in den vorherigen Commit squashen. Nur die Commit-Nachricht des vorherigen Commits wird verwendet.
      * `REBASE_OPERATION_EXEC`: keinen Commit cherry-picken. Führen Sie einen Befehl aus und fahren Sie fort, wenn der Befehl erfolgreich beendet wird.
  * `id`: der [`GitHash`](@ref) des Commits, an dem während dieses Rebase-Schrittes gearbeitet wird.
  * `exec`: falls `REBASE_OPERATION_EXEC` verwendet wird, der Befehl, der während dieses Schrittes ausgeführt werden soll (zum Beispiel das Test-Suite nach jedem Commit ausführen).
