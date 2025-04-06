```
reset!(repo::GitRepo, id::GitHash, mode::Cint=Consts.RESET_MIXED)
```

Depoyu `repo`'yu `id`'deki durumuna, `mode` ile belirlenen üç moddan birini kullanarak sıfırlayın:

1. `Consts.RESET_SOFT` - HEAD'i `id`'ye taşıyın.
2. `Consts.RESET_MIXED` - varsayılan, HEAD'i `id`'ye taşıyın ve dizini `id`'ye sıfırlayın.
3. `Consts.RESET_HARD` - HEAD'i `id`'ye taşıyın, dizini `id`'ye sıfırlayın ve tüm çalışma değişikliklerini atın.

# Örnekler

```julia
# değişiklikleri al
LibGit2.fetch(repo)
isfile(joinpath(repo_path, our_file)) # false dönecek

# değişiklikleri hızlı birleştir
LibGit2.merge!(repo, fastforward=true)

# çünkü yerel olarak herhangi bir dosya yoktu, ama
# uzakta bir dosya var, bu yüzden dalı sıfırlamamız gerekiyor
head_oid = LibGit2.head_oid(repo)
new_head = LibGit2.reset!(repo, head_oid, LibGit2.Consts.RESET_HARD)
```

Bu örnekte, alınan uzaktan *bir dosya* `our_file` adında bir dosya var, bu yüzden sıfırlamamız gerekiyor.

`git reset [--soft | --mixed | --hard] <id>` ile eşdeğerdir.

# Örnekler

```julia
repo = LibGit2.GitRepo(repo_path)
head_oid = LibGit2.head_oid(repo)
open(joinpath(repo_path, "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
mode = LibGit2.Consts.RESET_HARD
# file1'deki değişiklikleri atacak
# ve onu sahneden çıkaracak
new_head = LibGit2.reset!(repo, head_oid, mode)
```
