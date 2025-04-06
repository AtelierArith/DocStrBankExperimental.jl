```@meta
EditURL = "https://github.com/JuliaLang/Pkg.jl/blob/master/docs/src/basedocs.md"
```

# Pkg

Pkg ist Julias integrierter Paketmanager und verwaltet Vorgänge wie das Installieren, Aktualisieren und Entfernen von Paketen.

!!! note
    Was folgt, ist eine sehr kurze Einführung in Pkg. Für weitere Informationen zu `Project.toml`-Dateien, `Manifest.toml`-Dateien, der Kompatibilität von Paketversionen (`[compat]`), Umgebungen, Registrierungen usw. wird dringend empfohlen, das vollständige Handbuch zu lesen, das hier verfügbar ist: [https://pkgdocs.julialang.org](https://pkgdocs.julialang.org).


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
