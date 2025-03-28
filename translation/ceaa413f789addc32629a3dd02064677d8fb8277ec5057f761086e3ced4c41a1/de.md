```
LibGit2.RebaseOptions
```

Entspricht der `git_rebase_options`-Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Für jetzt immer `1`.
  * `quiet`: Informiert andere Git-Clients, die bei der Rebase helfen oder daran arbeiten, dass die Rebase "leise" durchgeführt werden soll. Wird für die Interoperabilität verwendet. Der Standardwert ist `1`.
  * `inmemory`: Startet eine In-Memory-Rebase. Aufrufer, die an der Rebase arbeiten, können die Schritte durchlaufen und Änderungen committen, aber HEAD nicht zurücksetzen oder das Repository aktualisieren. Das [`workdir`](@ref) wird nicht modifiziert. Nur vorhanden in libgit2-Versionen, die neuer oder gleich 0.24.0 sind.
  * `rewrite_notes_ref`: Name des Verweises auf Notizen, die verwendet werden, um die Commit-Notizen beim Abschluss der Rebase umzuschreiben.
  * `merge_opts`: Merge-Optionen, die steuern, wie die Bäume bei jedem Rebase-Schritt zusammengeführt werden. Nur vorhanden in libgit2-Versionen, die neuer oder gleich 0.24.0 sind.
  * `checkout_opts`: Checkout-Optionen zum Schreiben von Dateien beim Initialisieren der Rebase, beim Durchlaufen und beim Abbrechen. Siehe [`CheckoutOptions`](@ref) für weitere Informationen.
