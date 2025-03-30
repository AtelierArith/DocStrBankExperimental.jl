```
clone(repo_url::AbstractString, repo_path::AbstractString, clone_opts::CloneOptions)
```

`repo_url` (uzaktan bir URL veya yerel dosya sisteminde bir yol olabilir) üzerindeki uzaktan depoyu `repo_path` (yerel dosya sisteminde bir yol olmalıdır) konumuna klonlayın. Klonlama için seçenekler, örneğin, çıplak bir klon yapılıp yapılmayacağı gibi, [`CloneOptions`](@ref) ile ayarlanır.

# Örnekler

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo = LibGit2.clone(repo_url, "/home/me/projects/Example")
```
