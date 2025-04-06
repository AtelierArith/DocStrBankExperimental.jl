```
checkout!(repo::GitRepo, commit::AbstractString=""; force::Bool=true)
```

`git checkout [-f] --detach <commit>`와 동등합니다. `repo`에서 git 커밋 `commit`(문자열 형식의 [`GitHash`](@ref))을 체크아웃합니다. `force`가 `true`인 경우 체크아웃을 강제로 수행하고 현재 변경 사항을 모두 무시합니다. 현재 HEAD가 분리된다는 점에 유의하세요.

# 예제

```julia
repo = LibGit2.GitRepo(repo_path)
open(joinpath(LibGit2.path(repo), "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
commit_oid = LibGit2.commit(repo, "add file1")
open(joinpath(LibGit2.path(repo), "file1"), "w") do f
    write(f, "112
")
end
# force=true가 없으면 실패합니다.
# 파일에 수정 사항이 있기 때문입니다.
LibGit2.checkout!(repo, string(commit_oid), force=true)
```
