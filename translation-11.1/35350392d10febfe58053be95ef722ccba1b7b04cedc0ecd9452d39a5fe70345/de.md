```
LibGit2.CheckoutOptions
```

Entspricht der [`git_checkout_options`](https://libgit2.org/libgit2/#HEAD/type/git_checkout_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Für jetzt immer `1`.
  * `checkout_strategy`: Bestimmt, wie mit Konflikten umgegangen werden soll und ob der Checkout/das Wiederherstellen fehlender Dateien erzwungen werden soll.
  * `disable_filters`: Wenn ungleich null, keine Filter wie CLRF anwenden (um Zeilenumbrüche zwischen UNIX und DOS zu konvertieren).
  * `dir_mode`: Lese-/Schreib-/Zugriffsmodus für alle Verzeichnisse, die am Checkout beteiligt sind. Standard ist `0755`.
  * `file_mode`: Lese-/Schreib-/Zugriffsmodus für alle Dateien, die am Checkout beteiligt sind. Standard ist `0755` oder `0644`, abhängig vom Blob.
  * `file_open_flags`: Bitflags, die verwendet werden, um Dateien während des Checkouts zu öffnen.
  * `notify_flags`: Flags, für welche Art von Konflikten der Benutzer benachrichtigt werden sollte.
  * `notify_cb`: Eine optionale Callback-Funktion, um den Benutzer zu benachrichtigen, wenn ein Checkout-Konflikt auftritt. Wenn diese Funktion einen Wert ungleich null zurückgibt, wird der Checkout abgebrochen.
  * `notify_payload`: Payload für die Benachrichtigungs-Callback-Funktion.
  * `progress_cb`: Eine optionale Callback-Funktion, um den Fortschritt des Checkouts anzuzeigen.
  * `progress_payload`: Payload für den Fortschritts-Callback.
  * `paths`: Wenn nicht leer, beschreibt, welche Pfade während des Checkouts durchsucht werden sollen. Wenn leer, erfolgt der Checkout über alle Dateien im Repository.
  * `baseline`: Erwarteter Inhalt des [`workdir`](@ref), erfasst in einem (Zeiger auf ein) [`GitTree`](@ref). Standardmäßig der Zustand des Baums bei HEAD.
  * `baseline_index`: Erwarteter Inhalt des [`workdir`](@ref), erfasst in einem (Zeiger auf ein) `GitIndex`. Standardmäßig der Zustand des Index bei HEAD.
  * `target_directory`: Wenn nicht leer, Checkout in dieses Verzeichnis anstelle des `workdir`.
  * `ancestor_label`: Im Falle von Konflikten der Name der gemeinsamen Vorfahren-Seite.
  * `our_label`: Im Falle von Konflikten der Name der "unseren" Seite.
  * `their_label`: Im Falle von Konflikten der Name der "deren" Seite.
  * `perfdata_cb`: Eine optionale Callback-Funktion, um Leistungsdaten anzuzeigen.
  * `perfdata_payload`: Payload für den Leistungs-Callback.
