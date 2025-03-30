```
LibGit2.revcount(repo::GitRepo, commit1::AbstractString, commit2::AbstractString)
```

`commit1`과 `commit2` 사이의 수정 수를 나열합니다 (문자열 형식의 committish OID). `commit1`과 `commit2`가 서로 다른 브랜치에 있을 수 있으므로, `revcount`는 "왼쪽-오른쪽" 수정 목록(및 수)을 수행하여 각각 왼쪽 및 오른쪽 커밋 수를 포함하는 `Int`의 튜플을 반환합니다. 왼쪽(또는 오른쪽) 커밋은 커밋이 트리의 대칭 차이의 어느 쪽에서 도달 가능한지를 나타냅니다.

`git rev-list --left-right --count <commit1> <commit2>`와 동등합니다.

# 예제

```julia
repo = LibGit2.GitRepo(repo_path)
repo_file = open(joinpath(repo_path, test_file), "a")
println(repo_file, "hello world")
flush(repo_file)
LibGit2.add!(repo, test_file)
commit_oid1 = LibGit2.commit(repo, "commit 1")
println(repo_file, "hello world again")
flush(repo_file)
LibGit2.add!(repo, test_file)
commit_oid2 = LibGit2.commit(repo, "commit 2")
LibGit2.revcount(repo, string(commit_oid1), string(commit_oid2))
```

이것은 `(-1, 0)`을 반환합니다.
