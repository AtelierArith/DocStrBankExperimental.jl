```
LibGit2.StatusEntry
```

HEAD'deki dosya ile indeks arasındaki farkları ve indeks ile çalışma dizini arasındaki farkları sağlar. `git_status_entry` yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `status`: dosyanın durum bayraklarını içerir, dosyanın güncel olup olmadığını veya indeks veya çalışma ağacında bir şekilde değiştirilip değiştirilmediğini gösterir.
  * `head_to_index`: HEAD'deki dosya ile indeks arasındaki farkları kapsayan bir [`DiffDelta`](@ref) işaretçisidir.
  * `index_to_workdir`: indeks ile [`workdir`](@ref) arasındaki farkları kapsayan bir `DiffDelta` işaretçisidir.
