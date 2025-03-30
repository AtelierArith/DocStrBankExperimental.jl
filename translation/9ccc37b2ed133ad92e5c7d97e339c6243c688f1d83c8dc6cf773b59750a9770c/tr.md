```
GitObject(repo::GitRepo, hash::AbstractGitHash)
GitObject(repo::GitRepo, spec::AbstractString)
```

Belirtilen nesneyi ([`GitCommit`](@ref), [`GitBlob`](@ref), [`GitTree`](@ref) veya [`GitTag`](@ref)) `repo`'dan `hash`/`spec` ile belirtilen şekilde döndürün.

  * `hash`, tam (`GitHash`) veya kısmi (`GitShortHash`) bir hash'tir.
  * `spec`, tam liste için [git belgelerine](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) bakınız.
