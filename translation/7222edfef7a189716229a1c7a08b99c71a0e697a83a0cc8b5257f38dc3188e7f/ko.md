```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString, fetch_spec::AbstractString) -> GitRemote
```

원격 git 저장소를 저장소의 이름과 URL, 그리고 원격에서 가져오는 방법에 대한 사양(예: 어떤 원격 브랜치를 가져올지)을 사용하여 조회합니다.

# 예제

```julia
repo = LibGit2.init(repo_path)
refspec = "+refs/heads/mybranch:refs/remotes/origin/mybranch"
remote = LibGit2.GitRemote(repo, "upstream", repo_url, refspec)
```
