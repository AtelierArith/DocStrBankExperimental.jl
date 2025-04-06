```
LibGit2.shortname(ref::GitReference)
```

`ref`의 "인간이 읽을 수 있는" 이름의 축약 버전을 반환합니다.

```julia-repl
julia> repo = GitRepo(path_to_repo);

julia> branch_ref = LibGit2.head(repo);

julia> LibGit2.name(branch_ref)
"refs/heads/master"

julia> LibGit2.shortname(branch_ref)
"master"
```
