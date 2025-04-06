```
iscommit(id::AbstractString, repo::GitRepo) -> Bool
```

`id` (string biçiminde bir [`GitHash`](@ref)) olan commit'in depo içinde olup olmadığını kontrol eder.

# Örnekler

```julia-repl
julia> repo = GitRepo(repo_path);

julia> LibGit2.add!(repo, test_file);

julia> commit_oid = LibGit2.commit(repo, "add test_file");

julia> LibGit2.iscommit(string(commit_oid), repo)
true
```
