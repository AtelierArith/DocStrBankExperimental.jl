```
GitRemoteAnon(repo::GitRepo, url::AbstractString) -> GitRemote
```

URL만 사용하여 원격 git 저장소를 조회합니다. 이름은 사용하지 않습니다.

# 예제

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemoteAnon(repo, repo_url)
```
