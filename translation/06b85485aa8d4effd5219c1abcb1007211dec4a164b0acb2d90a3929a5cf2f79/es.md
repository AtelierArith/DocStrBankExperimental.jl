```
checkout!(repo::GitRepo, commit::AbstractString=""; force::Bool=true)
```

Equivalente a `git checkout [-f] --detach <commit>`. Realiza el checkout del commit de git `commit` (un [`GitHash`](@ref) en forma de cadena) en `repo`. Si `force` es `true`, fuerza el checkout y descarta cualquier cambio actual. Ten en cuenta que esto desacopla el HEAD actual.

# Ejemplos

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
# fallaría sin el force=true
# ya que hay modificaciones en el archivo
LibGit2.checkout!(repo, string(commit_oid), force=true)
```
