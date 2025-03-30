```
GitTree(repo::GitRepo, hash::AbstractGitHash)
GitTree(repo::GitRepo, spec::AbstractString)
```

`repo` tarafından belirtilen `hash`/`spec` ile bir `GitTree` nesnesi döndürün.

  * `hash`, tam (`GitHash`) veya kısmi (`GitShortHash`) bir hash'tir.
  * `spec`, metinsel bir spesifikasyondur: tam liste için [git belgelerine](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) bakın.
