```
clone(repo_url::AbstractString, repo_path::AbstractString, clone_opts::CloneOptions)
```

원격 저장소 `repo_url` (원격 URL 또는 로컬 파일 시스템의 경로일 수 있음)을 `repo_path` (로컬 파일 시스템의 경로여야 함)로 복제합니다. 복제 옵션, 예를 들어 베어 복제를 수행할지 여부는 [`CloneOptions`](@ref)로 설정됩니다.

# 예제

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo = LibGit2.clone(repo_url, "/home/me/projects/Example")
```
