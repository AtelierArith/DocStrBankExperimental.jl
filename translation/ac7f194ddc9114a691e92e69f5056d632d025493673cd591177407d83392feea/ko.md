```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString) -> GitRemote
```

원격 git 저장소를 이름과 URL을 사용하여 조회합니다. 기본 가져오기 refspec을 사용합니다.

# 예제

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemote(repo, "upstream", repo_url)
```
