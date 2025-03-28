```
LibGit2.MergeOptions
```

Entspricht der [`git_merge_options`](https://libgit2.org/libgit2/#HEAD/type/git_merge_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, falls sich dies später ändert. Für jetzt immer `1`.
  * `flags`: ein `enum` für Flags, die das Merge-Verhalten beschreiben. Definiert in [`git_merge_flag_t`](https://github.com/libgit2/libgit2/blob/HEAD/include/git2/merge.h#L95). Das entsprechende Julia-Enum ist `GIT_MERGE` und hat folgende Werte:

      * `MERGE_FIND_RENAMES`: erkennen, ob eine Datei zwischen dem gemeinsamen Vorfahren und der "unseren" oder "deren" Seite des Merges umbenannt wurde. Ermöglicht Merges, bei denen eine Datei umbenannt wurde.
      * `MERGE_FAIL_ON_CONFLICT`: sofort beenden, wenn ein Konflikt gefunden wird, anstatt zu versuchen, ihn zu lösen.
      * `MERGE_SKIP_REUC`: die REUC-Erweiterung nicht im Index zu schreiben, der aus dem Merge resultiert.
      * `MERGE_NO_RECURSIVE`: wenn die zusammengeführten Commits mehrere Merge-Basen haben, die erste verwenden, anstatt zu versuchen, die Basen rekursiv zu mergen.
  * `rename_threshold`: wie ähnlich zwei Dateien sein müssen, um eine als Umbenennung der anderen zu betrachten. Dies ist eine Ganzzahl, die die prozentuale Ähnlichkeit festlegt. Der Standardwert ist 50.
  * `target_limit`: die maximale Anzahl von Dateien, mit denen verglichen werden soll, um nach Umbenennungen zu suchen. Der Standardwert ist 200.
  * `metric`: optionale benutzerdefinierte Funktion, die verwendet wird, um die Ähnlichkeit zwischen zwei Dateien zur Erkennung von Umbenennungen zu bestimmen.
  * `recursion_limit`: die obere Grenze für die Anzahl der Merges von gemeinsamen Vorfahren, die durchgeführt werden sollen, um zu versuchen, eine neue virtuelle Merge-Basis für den Merge zu erstellen. Der Standardwert ist keine Grenze. Dieses Feld ist nur in libgit2-Versionen neuer als 0.24.0 vorhanden.
  * `default_driver`: der Merge-Treiber, der verwendet werden soll, wenn beide Seiten geändert wurden. Dieses Feld ist nur in libgit2-Versionen neuer als 0.25.0 vorhanden.
  * `file_favor`: wie mit konfliktierenden Dateiinhalten für den `text`-Treiber umgegangen werden soll.

      * `MERGE_FILE_FAVOR_NORMAL`: wenn beide Seiten des Merges Änderungen an einem Abschnitt haben, eine Notiz über den Konflikt im Index machen, den `git checkout` verwenden wird, um eine Merge-Datei zu erstellen, auf die der Benutzer dann verweisen kann, um die Konflikte zu lösen. Dies ist der Standard.
      * `MERGE_FILE_FAVOR_OURS`: wenn beide Seiten des Merges Änderungen an einem Abschnitt haben, die Version auf der "unseren" Seite des Merges im Index verwenden.
      * `MERGE_FILE_FAVOR_THEIRS`: wenn beide Seiten des Merges Änderungen an einem Abschnitt haben, die Version auf der "deren" Seite des Merges im Index verwenden.
      * `MERGE_FILE_FAVOR_UNION`: wenn beide Seiten des Merges Änderungen an einem Abschnitt haben, jede einzigartige Zeile von beiden Seiten in die Datei einfügen, die in den Index aufgenommen wird.
  * `file_flags`: Richtlinien für das Mergen von Dateien.
