```
LibGit2.DescribeOptions
```

Entspricht der [`git_describe_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_options) Struktur.

Die Felder repräsentieren:

  * `version`: Version der verwendeten Struktur, für den Fall, dass sich dies später ändert. Für jetzt immer `1`.
  * `max_candidates_tags`: Berücksichtige so viele der aktuellsten Tags in `refs/tags`, um einen Commit zu beschreiben. Standardmäßig 10 (so dass die 10 aktuellsten Tags untersucht werden, um zu sehen, ob sie einen Commit beschreiben).
  * `describe_strategy`: ob alle Einträge in `refs/tags` (entspricht `git-describe --tags`) oder alle Einträge in `refs/` (entspricht `git-describe --all`) berücksichtigt werden sollen. Der Standard ist, nur annotierte Tags anzuzeigen. Wenn `Consts.DESCRIBE_TAGS` übergeben wird, werden alle Tags, annotiert oder nicht, berücksichtigt. Wenn `Consts.DESCRIBE_ALL` übergeben wird, wird jeder Ref in `refs/` berücksichtigt.
  * `pattern`: Berücksichtige nur Tags, die mit `pattern` übereinstimmen. Unterstützt Glob-Erweiterung.
  * `only_follow_first_parent`: Beim Finden der Distanz von einem übereinstimmenden Verweis zum beschriebenen Objekt, nur die Distanz vom ersten Elternteil berücksichtigen.
  * `show_commit_oid_as_fallback`: Wenn kein übereinstimmender Verweis gefunden werden kann, der einen Commit beschreibt, zeige den Commit's [`GitHash`](@ref) anstelle eines Fehlers (das Standardverhalten).
