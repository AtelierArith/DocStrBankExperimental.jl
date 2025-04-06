```
iscommit(id::AbstractString, repo::GitRepo) -> Bool
```

Verifica si el commit `id` (que es un [`GitHash`](@ref) en forma de cadena) está en el repositorio.

# Ejemplos

```julia-repl
julia> repo = GitRepo(repo_path);

julia> LibGit2.add!(repo, test_file);

julia> commit_oid = LibGit2.commit(repo, "add test_file");

julia> LibGit2.iscommit(string(commit_oid), repo)
true
```
