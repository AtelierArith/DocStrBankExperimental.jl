```
diff_files(repo::GitRepo, branch1::AbstractString, branch2::AbstractString; kwarg...) -> Vector{AbstractString}
```

Git deposunda `repo` arasında `branch1` ve `branch2` dalları arasında hangi dosyaların değiştiğini gösterir.

Anahtar argümanı:

  * `filter::Set{Consts.DELTA_STATUS}=Set([Consts.DELTA_ADDED, Consts.DELTA_MODIFIED, Consts.DELTA_DELETED]))`, ve diff için seçenekleri ayarlar. Varsayılan, eklenen, değiştirilen veya silinen dosyaları göstermektir.

Değişen dosyaların yalnızca *isimlerini* döndürün, *içeriklerini* değil.

# Örnekler

```julia
LibGit2.branch!(repo, "branch/a")
LibGit2.branch!(repo, "branch/b")
# repo'ya bir dosya ekle
open(joinpath(LibGit2.path(repo),"file"),"w") do f
    write(f, "hello repo
")
end
LibGit2.add!(repo, "file")
LibGit2.commit(repo, "add file")
# ["file"] döner
filt = Set([LibGit2.Consts.DELTA_ADDED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
# mevcut dosyalar değiştirilmediği için [] döner
filt = Set([LibGit2.Consts.DELTA_MODIFIED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
```

`git diff --name-only --diff-filter=<filter> <branch1> <branch2>` ile eşdeğerdir.
