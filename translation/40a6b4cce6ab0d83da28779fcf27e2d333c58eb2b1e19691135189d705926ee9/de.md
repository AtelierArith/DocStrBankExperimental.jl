```
iscommit(id::AbstractString, repo::GitRepo) -> Bool
```

Überprüfen, ob der Commit `id` (der in Form eines [`GitHash`](@ref) als Zeichenkette vorliegt) im Repository vorhanden ist.

# Beispiele

```julia-repl
julia> repo = GitRepo(repo_path);

julia> LibGit2.add!(repo, test_file);

julia> commit_oid = LibGit2.commit(repo, "add test_file");

julia> LibGit2.iscommit(string(commit_oid), repo)
true
```
