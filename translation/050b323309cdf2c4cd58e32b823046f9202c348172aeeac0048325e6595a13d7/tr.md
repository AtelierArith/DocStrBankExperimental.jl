```
find_artifacts_toml(path::String)
```

Bir `.jl` dosyasının yolunu vererek (örneğin, bir makro bağlamında `__source__.file` ile döndürülen), içindeki projede bulunan `(Julia)Artifacts.toml` dosyasını bulur (varsa), aksi takdirde `nothing` döner.

!!! compat "Julia 1.3"
    Bu fonksiyon en az Julia 1.3 gerektirir.

