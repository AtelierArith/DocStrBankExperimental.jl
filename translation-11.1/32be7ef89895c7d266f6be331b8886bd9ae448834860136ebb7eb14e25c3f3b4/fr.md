```@meta
EditURL = "https://github.com/JuliaLang/Pkg.jl/blob/master/docs/src/basedocs.md"
```

# Pkg

Pkg est le gestionnaire de paquets intégré de Julia, et gère des opérations telles que l'installation, la mise à jour et la suppression de paquets.

!!! note
    Ce qui suit est une très brève introduction à Pkg. Pour plus d'informations sur les fichiers `Project.toml`, les fichiers `Manifest.toml`, la compatibilité des versions de package (`[compat]`), les environnements, les registres, etc., il est fortement recommandé de lire le manuel complet, qui est disponible ici : [https://pkgdocs.julialang.org](https://pkgdocs.julialang.org).


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
