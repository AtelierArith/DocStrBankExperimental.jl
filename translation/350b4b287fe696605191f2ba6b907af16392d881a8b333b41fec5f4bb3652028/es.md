```
LibGit2.shortname(ref::GitReference)
```

Devuelve una versión abreviada del nombre de `ref` que es "legible por humanos".

```julia-repl
julia> repo = GitRepo(path_to_repo);

julia> branch_ref = LibGit2.head(repo);

julia> LibGit2.name(branch_ref)
"refs/heads/master"

julia> LibGit2.shortname(branch_ref)
"master"
```
