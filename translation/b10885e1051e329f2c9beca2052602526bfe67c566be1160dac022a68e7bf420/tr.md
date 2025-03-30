```
LibGit2.read_tree!(idx::GitIndex, tree::GitTree)
LibGit2.read_tree!(idx::GitIndex, treehash::AbstractGitHash)
```

Ağaç `tree`'i (veya `idx` tarafından sahip olunan depodaki `treehash` ile işaretlenen ağacı) `idx` dizinine oku. Mevcut dizin içeriği değiştirilecektir.
