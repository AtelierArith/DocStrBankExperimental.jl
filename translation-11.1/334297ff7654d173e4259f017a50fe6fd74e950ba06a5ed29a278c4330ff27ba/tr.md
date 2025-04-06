```
LibGit2.path(repo::GitRepo)
```

Depo `repo`'nun temel dosya yolunu döndürür.

  * normal depolar için, bu genellikle ".git" dizininin üst dizini olacaktır (not: bu, çalışma dizininden farklı olabilir, daha fazla bilgi için `workdir`'e bakın).
  * çıplak depolar için, bu "git" dosyalarının konumudur.

Ayrıca bkz. [`gitdir`](@ref), [`workdir`](@ref).
