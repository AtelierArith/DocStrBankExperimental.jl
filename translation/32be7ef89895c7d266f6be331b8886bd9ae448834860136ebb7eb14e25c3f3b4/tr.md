```@meta
EditURL = "https://github.com/JuliaLang/Pkg.jl/blob/master/docs/src/basedocs.md"
```

# Pkg

Pkg, Julia'nın yerleşik paket yöneticisidir ve paketleri yükleme, güncelleme ve kaldırma gibi işlemleri yönetir.

!!! note
    Aşağıda Pkg hakkında çok kısa bir tanıtım bulunmaktadır. `Project.toml` dosyaları, `Manifest.toml` dosyaları, paket sürüm uyumluluğu (`[compat]`), ortamlar, kayıt defterleri vb. hakkında daha fazla bilgi için, burada mevcut olan tam kılavuzu okumanız şiddetle tavsiye edilir: [https://pkgdocs.julialang.org](https://pkgdocs.julialang.org).


```@eval
import Markdown
file = joinpath(Sys.STDLIB, "Pkg", "docs", "src", "getting-started.md")
str = read(file, String)
str = replace(str, r"^#.*$"m => "")
str = replace(str, "[API Reference](@ref)" => "[API Reference](https://pkgdocs.julialang.org/v1/api/)")
str = replace(str, "(@ref Working-with-Environments)" => "(https://pkgdocs.julialang.org/v1/environments/)")
str = replace(str, "(@ref Managing-Packages)" => "(https://pkgdocs.julialang.org/v1/managing-packages/)")
Markdown.parse(str)
```
