```
LibGit2.shortname(ref::GitReference)
```

Gibt eine verkürzte Version des Namens von `ref` zurück, die "menschlich lesbar" ist.

```julia-repl
julia> repo = GitRepo(path_to_repo);

julia> branch_ref = LibGit2.head(repo);

julia> LibGit2.name(branch_ref)
"refs/heads/master"

julia> LibGit2.shortname(branch_ref)
"master"
```
