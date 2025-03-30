```
LibGit2.isdiff(repo::GitRepo, treeish::AbstractString, pathspecs::AbstractString=""; cached::Bool=false)
```

`treeish`로 지정된 트리와 작업 트리의 추적 파일(만약 `cached=false`인 경우) 또는 인덱스(만약 `cached=true`인 경우) 간의 차이가 있는지 확인합니다. `pathspecs`는 diff에 대한 옵션의 사양입니다.

# 예제

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdiff(repo, "HEAD") # false여야 함
open(joinpath(repo_path, new_file), "a") do f
    println(f, "여기 내 멋진 새 파일이 있어요")
end
LibGit2.isdiff(repo, "HEAD") # 이제 true
```

`git diff-index <treeish> [-- <pathspecs>]`와 동등합니다.
