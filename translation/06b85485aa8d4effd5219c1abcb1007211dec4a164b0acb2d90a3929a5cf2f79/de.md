```
checkout!(repo::GitRepo, commit::AbstractString=""; force::Bool=true)
```

Entspricht `git checkout [-f] --detach <commit>`. Wechselt zu dem git-Commit `commit` (ein [`GitHash`](@ref) in String-Form) in `repo`. Wenn `force` `true` ist, wird der Checkout erzwungen und alle aktuellen Änderungen verworfen. Beachten Sie, dass dies den aktuellen HEAD abtrennt.

# Beispiele

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
# würde ohne force=true fehlschlagen
# da es Änderungen an der Datei gibt
LibGit2.checkout!(repo, string(commit_oid), force=true)
```
