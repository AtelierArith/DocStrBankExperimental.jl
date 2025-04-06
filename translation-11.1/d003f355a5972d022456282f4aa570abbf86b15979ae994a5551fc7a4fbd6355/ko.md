```
LibGit2.isdirty(repo::GitRepo, pathspecs::AbstractString=""; cached::Bool=false) -> Bool
```

작업 트리에서 추적된 파일에 변경 사항이 있는지 확인합니다(만약 `cached=false`인 경우) 또는 인덱스에서(만약 `cached=true`인 경우). `pathspecs`는 diff에 대한 옵션의 사양입니다.

# 예제

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdirty(repo) # false여야 합니다
open(joinpath(repo_path, new_file), "a") do f
    println(f, "여기 내 멋진 새 파일이 있어요")
end
LibGit2.isdirty(repo) # 이제 true입니다
LibGit2.isdirty(repo, new_file) # 이제 true입니다
```

`git diff-index HEAD [-- <pathspecs>]`와 동등합니다.
