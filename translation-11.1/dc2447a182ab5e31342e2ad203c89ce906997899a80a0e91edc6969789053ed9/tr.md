```
branch!(repo::GitRepo, branch_name::AbstractString, commit::AbstractString=""; kwargs...)
```

`repo` deposunda yeni bir git dalı oluşturur. `commit`, yeni dalın başlangıcı olacak olan, string biçimindeki [`GitHash`](@ref) dir. Eğer `commit` boş bir string ise, mevcut HEAD kullanılacaktır.

Anahtar argümanlar şunlardır:

  * `track::AbstractString=""`: bu yeni dalın takip etmesi gereken uzak dalın adı, varsa. Boşsa (varsayılan), hiçbir uzak dal takip edilmeyecektir.
  * `force::Bool=false`: eğer `true` ise, dal oluşturma zorlanacaktır.
  * `set_head::Bool=true`: eğer `true` ise, dal oluşturma işlemi tamamlandıktan sonra dal başı `repo`'nun HEAD'i olarak ayarlanacaktır.

`git checkout [-b|-B] <branch_name> [<commit>] [--track <track>]` ile eşdeğerdir.

# Örnekler

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.branch!(repo, "new_branch", set_head=false)
```
