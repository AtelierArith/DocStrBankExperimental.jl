```
clone(repo_url::AbstractString, repo_path::AbstractString; kwargs...)
```

`repo_url`'da bulunan bir uzak deposunu yerel dosya sistemi konumu `repo_path`'a klonlayın.

Anahtar argümanlar şunlardır:

  * `branch::AbstractString=""`: varsayılan depo dalı (genellikle `master`) değilse, klonlanacak uzak dal.
  * `isbare::Bool=false`: `true` ise, uzak depoyu çıplak bir depo olarak klonlayın, bu `repo_path`'ın kendisini git dizini yapar, `repo_path/.git` yerine. Bu, bir çalışma ağacının kontrol edilemeyeceği anlamına gelir. Git CLI argümanı `--bare` rolünü oynar.
  * `remote_cb::Ptr{Cvoid}=C_NULL`: klonlanmadan önce uzak depoyu oluşturmak için kullanılacak bir geri çağırma. `C_NULL` (varsayılan) ise, uzak deponun oluşturulması için herhangi bir girişimde bulunulmayacak - zaten var olduğu varsayılacaktır.
  * `credentials::Creds=nothing`: özel bir depoya karşı kimlik doğrularken kimlik bilgileri ve/veya ayarlar sağlar.
  * `callbacks::Callbacks=Callbacks()`: kullanıcı tarafından sağlanan geri çağırmalar ve yükler.

`git clone [-b <branch>] [--bare] <repo_url> <repo_path>` ile eşdeğerdir.

# Örnekler

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo1 = LibGit2.clone(repo_url, "test_path")
repo2 = LibGit2.clone(repo_url, "test_path", isbare=true)
julia_url = "https://github.com/JuliaLang/julia"
julia_repo = LibGit2.clone(julia_url, "julia_path", branch="release-0.6")
```
