```@meta
EditURL = "https://github.com/JuliaLang/Pkg.jl/blob/master/docs/src/basedocs.md"
```

# Pkg

Pkg es el gestor de paquetes integrado de Julia y maneja operaciones como la instalación, actualización y eliminación de paquetes.

!!! note
    A continuación se presenta una introducción muy breve a Pkg. Para obtener más información sobre los archivos `Project.toml`, los archivos `Manifest.toml`, la compatibilidad de versiones de paquetes (`[compat]`), entornos, registros, etc., se recomienda encarecidamente leer el manual completo, que está disponible aquí: [https://pkgdocs.julialang.org](https://pkgdocs.julialang.org).


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
