```
diff_files(repo::GitRepo, branch1::AbstractString, branch2::AbstractString; kwarg...) -> Vector{AbstractString}
```

`repo`라는 git 저장소에서 `branch1`과 `branch2` 사이에 변경된 파일을 보여줍니다.

키워드 인자는 다음과 같습니다:

  * `filter::Set{Consts.DELTA_STATUS}=Set([Consts.DELTA_ADDED, Consts.DELTA_MODIFIED, Consts.DELTA_DELETED]))`이며, diff에 대한 옵션을 설정합니다. 기본값은 추가, 수정 또는 삭제된 파일을 보여주는 것입니다.

변경된 파일의 *이름*만 반환하며, *내용*은 반환하지 않습니다.

# 예시

```julia
LibGit2.branch!(repo, "branch/a")
LibGit2.branch!(repo, "branch/b")
# repo에 파일 추가
open(joinpath(LibGit2.path(repo),"file"),"w") do f
    write(f, "hello repo
")
end
LibGit2.add!(repo, "file")
LibGit2.commit(repo, "add file")
# ["file"] 반환
filt = Set([LibGit2.Consts.DELTA_ADDED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
# 기존 파일이 수정되지 않았으므로 [] 반환
filt = Set([LibGit2.Consts.DELTA_MODIFIED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
```

`git diff --name-only --diff-filter=<filter> <branch1> <branch2>`와 동등합니다.
