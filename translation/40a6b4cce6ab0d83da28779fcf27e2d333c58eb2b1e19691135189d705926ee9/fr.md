```
iscommit(id::AbstractString, repo::GitRepo) -> Bool
```

Vérifiez si le commit `id` (qui est un [`GitHash`](@ref) sous forme de chaîne) est dans le dépôt.

# Exemples

```julia-repl
julia> repo = GitRepo(repo_path);

julia> LibGit2.add!(repo, test_file);

julia> commit_oid = LibGit2.commit(repo, "ajouter test_file");

julia> LibGit2.iscommit(string(commit_oid), repo)
true
```
