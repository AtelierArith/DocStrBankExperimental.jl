```
GitBlob(repo::GitRepo, hash::AbstractGitHash)
GitBlob(repo::GitRepo, spec::AbstractString)
```

`repo` tarafından `hash`/`spec` ile belirtilen bir `GitBlob` nesnesi döndürün.

  * `hash` tam (`GitHash`) veya kısmi (`GitShortHash`) bir hash'tir.
  * `spec` metinsel bir spesifikasyondur: tam liste için [git belgelerine](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) bakın.
