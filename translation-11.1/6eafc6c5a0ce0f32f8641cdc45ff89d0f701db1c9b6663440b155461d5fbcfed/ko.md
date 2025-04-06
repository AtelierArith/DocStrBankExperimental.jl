```
reset!(repo::GitRepo, id::GitHash, mode::Cint=Consts.RESET_MIXED)
```

저장소 `repo`를 `id`의 상태로 재설정하며, `mode`에 의해 설정된 세 가지 모드 중 하나를 사용합니다:

1. `Consts.RESET_SOFT` - HEAD를 `id`로 이동합니다.
2. `Consts.RESET_MIXED` - 기본값, HEAD를 `id`로 이동하고 인덱스를 `id`로 재설정합니다.
3. `Consts.RESET_HARD` - HEAD를 `id`로 이동하고 인덱스를 `id`로 재설정하며 모든 작업 변경 사항을 버립니다.

# 예제

```julia
# 변경 사항 가져오기
LibGit2.fetch(repo)
isfile(joinpath(repo_path, our_file)) # false가 될 것입니다.

# 변경 사항을 패스트 포워드 병합
LibGit2.merge!(repo, fastforward=true)

# 로컬에 파일이 없지만 원격에 파일이 있기 때문에
# 브랜치를 재설정해야 합니다.
head_oid = LibGit2.head_oid(repo)
new_head = LibGit2.reset!(repo, head_oid, LibGit2.Consts.RESET_HARD)
```

이 예제에서 가져오는 원격에는 인덱스에 `our_file`이라는 파일이 존재하므로 재설정해야 합니다.

`git reset [--soft | --mixed | --hard] <id>`와 동등합니다.

# 예제

```julia
repo = LibGit2.GitRepo(repo_path)
head_oid = LibGit2.head_oid(repo)
open(joinpath(repo_path, "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
mode = LibGit2.Consts.RESET_HARD
# file1에 대한 변경 사항을 버리고
# 스테이징 해제합니다.
new_head = LibGit2.reset!(repo, head_oid, mode)
```
