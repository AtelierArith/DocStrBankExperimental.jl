```@meta
EditURL = "https://github.com/JuliaLang/Pkg.jl/blob/master/docs/src/basedocs.md"
```

# Pkg

Pkg 是 Julia 的内置包管理器，处理安装、更新和删除包等操作。

!!! note
    以下是对Pkg的简要介绍。有关`Project.toml`文件、`Manifest.toml`文件、包版本兼容性（`[compat]`）、环境、注册表等的更多信息，强烈建议阅读完整手册，手册可在此处获取：[https://pkgdocs.julialang.org](https://pkgdocs.julialang.org)。


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
