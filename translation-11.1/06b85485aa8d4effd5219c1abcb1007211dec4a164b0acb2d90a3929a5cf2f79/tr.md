```
checkout!(repo::GitRepo, commit::AbstractString=""; force::Bool=true)
```

Eşdeğer `git checkout [-f] --detach <commit>`. `repo` içindeki git commit `commit`'i (bir [`GitHash`](@ref) string biçiminde) kontrol et. Eğer `force` `true` ise, kontrolü zorla ve mevcut değişiklikleri yok say. Bu, mevcut HEAD'i ayırır.

# Örnekler

```julia
repo = LibGit2.GitRepo(repo_path)
open(joinpath(LibGit2.path(repo), "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
commit_oid = LibGit2.commit(repo, "add file1")
open(joinpath(LibGit2.path(repo), "file1"), "w") do f
    write(f, "112
")
end
# force=true olmadan başarısız olur
# çünkü dosyada değişiklikler var
LibGit2.checkout!(repo, string(commit_oid), force=true)
```
