```
LibGit2.init(path::AbstractString, bare::Bool=false) -> GitRepo
```

`path`'te yeni bir git deposu açar. Eğer `bare` `false` ise, çalışma ağacı `path/.git` içinde oluşturulacaktır. Eğer `bare` `true` ise, hiçbir çalışma dizini oluşturulmayacaktır.
