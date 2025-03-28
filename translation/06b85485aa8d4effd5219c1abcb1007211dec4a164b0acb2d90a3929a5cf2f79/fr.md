```
checkout!(repo::GitRepo, commit::AbstractString=""; force::Bool=true)
```

Équivalent à `git checkout [-f] --detach <commit>`. Effectue le checkout du commit git `commit` (un [`GitHash`](@ref) sous forme de chaîne) dans `repo`. Si `force` est `true`, force le checkout et abandonne toutes les modifications en cours. Notez que cela détache le HEAD actuel.

# Exemples

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
# échouerait sans le force=true
# puisque le fichier a des modifications
LibGit2.checkout!(repo, string(commit_oid), force=true)
```
