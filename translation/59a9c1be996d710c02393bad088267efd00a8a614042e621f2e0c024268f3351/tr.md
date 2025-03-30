```
LibGit2.isdiff(repo::GitRepo, treeish::AbstractString, pathspecs::AbstractString=""; cached::Bool=false)
```

`treeish` tarafından belirtilen ağaç ile çalışma ağacındaki izlenen dosyalar (eğer `cached=false` ise) veya indeks (eğer `cached=true` ise) arasındaki herhangi bir fark olup olmadığını kontrol eder. `pathspecs`, diff için seçeneklerin spesifikasyonlarıdır.

# Örnekler

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdiff(repo, "HEAD") # false olmalı
open(joinpath(repo_path, new_file), "a") do f
    println(f, "işte benim harika yeni dosyam")
end
LibGit2.isdiff(repo, "HEAD") # şimdi true
```

`git diff-index <treeish> [-- <pathspecs>]` ile eşdeğerdir.
