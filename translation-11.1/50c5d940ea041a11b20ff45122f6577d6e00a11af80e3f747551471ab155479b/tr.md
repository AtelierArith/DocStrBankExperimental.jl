```
GitAnnotated(repo::GitRepo, commit_id::GitHash)
GitAnnotated(repo::GitRepo, ref::GitReference)
GitAnnotated(repo::GitRepo, fh::FetchHead)
GitAnnotated(repo::GitRepo, committish::AbstractString)
```

Açıklamalı bir git komiti, nasıl bulunduğu ve nedenine dair bilgi taşır, böylece yeniden temel alma veya birleştirme işlemleri, komitin bağlamı hakkında daha fazla bilgiye sahip olur. Çatışma dosyaları, örneğin, birleştirmedeki çelişen kaynak/hedef dallar hakkında bilgi içerir. Açıklamalı bir komit, örneğin bir [`FetchHead`](@ref) geçirildiğinde, bir uzak dalın ucuna veya `GitReference` kullanılarak tanımlanan bir dal başına atıfta bulunabilir.
