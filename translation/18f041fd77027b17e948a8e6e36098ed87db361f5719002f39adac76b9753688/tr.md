```
LibGit2.reftype(ref::GitReference) -> Cint
```

`ref`'in türüne karşılık gelen bir `Cint` döndür:

  * Referans geçersizse `0`
  * Referans bir nesne kimliği ise `1`
  * Referans sembolikse `2`
