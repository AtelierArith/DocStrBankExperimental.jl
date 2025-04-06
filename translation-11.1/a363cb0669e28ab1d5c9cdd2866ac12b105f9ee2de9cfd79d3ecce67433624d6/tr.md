```
LibGit2.GitStatus(repo::GitRepo; status_opts=StatusOptions())
```

Git deposunda `repo` her dosyanın durumunu (örneğin, dosya değiştirilmiş mi, sahnelenmiş mi, vb.) hakkında bilgi toplar. `status_opts`, izlenmeyen dosyaları kontrol edip etmeyeceğiniz veya alt modülleri dahil edip etmeyeceğiniz gibi çeşitli seçenekleri ayarlamak için kullanılabilir. Daha fazla bilgi için [`StatusOptions`](@ref) bakın.
