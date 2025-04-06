```
GitTag(repo::GitRepo, hash::AbstractGitHash)
GitTag(repo::GitRepo, spec::AbstractString)
```

`repo` tarafından `hash`/`spec` ile belirtilen bir `GitTag` nesnesi döndürün.

  * `hash` tam (`GitHash`) veya kısmi (`GitShortHash`) bir hash'tir.
  * `spec` bir metin spesifikasyonudur: tam liste için [git belgelerine](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) bakın.
