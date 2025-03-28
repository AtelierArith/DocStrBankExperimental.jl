```
LibGit2.DiffOptionsStruct
```

Entspricht der [`git_diff_options`](https://libgit2.org/libgit2/#HEAD/type/git_diff_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Derzeit immer `1`.
  * `flags`: Flags, die steuern, welche Dateien im Diff erscheinen. Standardmäßig `DIFF_NORMAL`.
  * `ignore_submodules`: ob Dateien in Submodulen betrachtet werden sollen oder nicht. Standardmäßig `SUBMODULE_IGNORE_UNSPECIFIED`, was bedeutet, dass die Konfiguration des Submoduls steuert, ob es im Diff erscheint oder nicht.
  * `pathspec`: Pfad zu Dateien, die im Diff enthalten sein sollen. Standard ist die Verwendung aller Dateien im Repository.
  * `notify_cb`: optionale Callback-Funktion, die den Benutzer über Änderungen am Diff informiert, während Dateideltas hinzugefügt werden.
  * `progress_cb`: optionale Callback-Funktion, die den Fortschritt des Diffs anzeigt. Nur relevant bei libgit2-Versionen, die mindestens so neu sind wie 0.24.0.
  * `payload`: die Nutzlast, die an `notify_cb` und `progress_cb` übergeben wird.
  * `context_lines`: die Anzahl der *unveränderten* Zeilen, die verwendet werden, um die Ränder eines Hunk zu definieren. Dies ist auch die Anzahl der Zeilen, die vor/nach einem Hunk angezeigt werden, um Kontext bereitzustellen. Standard ist 3.
  * `interhunk_lines`: die maximale Anzahl von *unveränderten* Zeilen *zwischen* zwei separaten Hunks, die erlaubt sind, bevor die Hunks kombiniert werden. Standard ist 0.
  * `id_abbrev`: legt die Länge des abgekürzten [`GitHash`](@ref) fest, die gedruckt werden soll. Standard ist `7`.
  * `max_size`: die maximale Dateigröße eines Blobs. Über dieser Größe wird es als binärer Blob behandelt. Der Standardwert beträgt 512 MB.
  * `old_prefix`: das virtuelle Verzeichnis, in dem alte Dateien auf einer Seite des Diffs platziert werden. Der Standardwert ist `"a"`.
  * `new_prefix`: das virtuelle Verzeichnis, in dem neue Dateien auf einer Seite des Diffs platziert werden. Der Standardwert ist `"b"`.
