```
LibGit2.shortname(ref::GitReference)
```

`ref`'in kısaltılmış, "insan tarafından okunabilir" bir versiyonunu döndürür.

```julia-repl
julia> repo = GitRepo(path_to_repo);

julia> branch_ref = LibGit2.head(repo);

julia> LibGit2.name(branch_ref)
"refs/heads/master"

julia> LibGit2.shortname(branch_ref)
"master"
```
