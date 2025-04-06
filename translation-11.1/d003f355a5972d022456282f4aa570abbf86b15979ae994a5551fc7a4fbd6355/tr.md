```
LibGit2.isdirty(repo::GitRepo, pathspecs::AbstractString=""; cached::Bool=false) -> Bool
```

Çalışma ağacındaki (eğer `cached=false` ise) veya dizindeki (eğer `cached=true` ise) izlenen dosyalarda herhangi bir değişiklik olup olmadığını kontrol eder. `pathspecs`, fark için seçeneklerin spesifikasyonlarıdır.

# Örnekler

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdirty(repo) # false olmalı
open(joinpath(repo_path, new_file), "a") do f
    println(f, "işte benim harika yeni dosyam")
end
LibGit2.isdirty(repo) # şimdi true
LibGit2.isdirty(repo, new_file) # şimdi true
```

`git diff-index HEAD [-- <pathspecs>]` ile eşdeğerdir.
