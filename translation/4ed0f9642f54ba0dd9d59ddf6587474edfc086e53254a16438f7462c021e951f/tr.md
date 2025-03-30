```
LibGit2.workdir(repo::GitRepo)
```

`repo`'nun çalışma dizininin konumunu döndürür. Bu, çıplak depolar için bir hata verecektir.

!!! not
    Bu genellikle `gitdir(repo)`'nun üst dizini olacaktır, ancak bazı durumlarda farklı olabilir: örneğin, `core.worktree` yapılandırma değişkeni veya `GIT_WORK_TREE` ortam değişkeni ayarlanmışsa.


Ayrıca bkz. [`gitdir`](@ref), [`path`](@ref).
