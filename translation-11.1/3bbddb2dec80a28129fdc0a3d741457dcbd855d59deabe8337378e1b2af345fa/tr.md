```
set_remote_url(repo::GitRepo, remote_name, url)
set_remote_url(repo::String, remote_name, url)
```

`remote_name` için hem fetch hem de push `url`'sini [`GitRepo`](@ref) veya `path`'te bulunan git deposu için ayarlayın. Genellikle git reposu `"origin"`'i uzak ad olarak kullanır.

# Örnekler

```julia
repo_path = joinpath(tempdir(), "Example")
repo = LibGit2.init(repo_path)
LibGit2.set_remote_url(repo, "upstream", "https://github.com/JuliaLang/Example.jl")
LibGit2.set_remote_url(repo_path, "upstream2", "https://github.com/JuliaLang/Example2.jl")
```
